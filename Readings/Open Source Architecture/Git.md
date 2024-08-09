Keywords: #bash #git #design
Lecture link: here
## What is Git?

Git enables the maintenance of a digital body of work (often, but not limited to, code) by many collaborators using a peer-to-peer network of repositories. It supports distributed workflows, allowing a body of work to either eventually converge or temporarily diverge.

## Origin

Linux Kernel community is the one responsible for this awesome project, if you understand their context, you easily understand why Git is the way it is.

The Linux Kernel is a massive project, with a lot of contributors working at the same time, in that particular time, they were unable to find a VCS (Version Control System) to handle that v0lume.

Git is an open source project that born out of those needs and frustrations in 2005. Before that Linux used BitKeeper and CVS, by different core developers. 

Days after BitMover, announced it would revoke the licenses of some core Linux kernel developers, Linus Tovard started working on Git.

He began by writing a collection of scripts to help him manage email patches to apply one after the other. The aim of this initial collection of scripts was to be able to abort merges quickly so the maintainer could modify the codebase mid-patch-stream to manually merge, then continue merging subsequent patches

The main goal in their philosophical goal was:
- Support distributed workflows similar to those enabled by BitKeeper
- Offer safeguards against content corruption
- Offer high performance

> [!IMPORTANT] Git uses DAGs (Directed Acyclic Graphs) for enable all of this. Kudos to Discrete math

Distributed version control systems offer great workflow flexibility, often at the expense of simplicity. Specific benefits of a distributed model include:

- Providing the ability for collaborators to work offline and commit incrementally.
- Allowing a collaborator to determine when his/her work is ready to share.
- Offering the collaborator access to the repository history when offline.
- Allowing the managed work to be published to multiple repositories, potentially with different branches or granularity of changes visible.

## How to design my own VCS

We must ensure at least always 3 things:

- Storing content
- Tracking changes to the content (history including merge metadata)
- Distributing the content and history with collaborators

### Content Storage

We can use two of the most common approaches, such as DAGs or delta-based changeset.

Delta-based changesets encapsulate the differences between two versions of the flattened content, plus some metadata.

Representing content as a directed acyclic graph involves objects forming a hierarchy which mirrors the content's filesystem tree as a snapshot of the commit (reusing the unchanged objects inside the tree where possible).

 Git stores content as a directed acyclic graph using different types of objects.

### Commit and Merge Histories

On the history and change-tracking front most VCS software uses one of the following approaches:

- Linear history
- Directed acyclic graph for history

Git build this around DAGs

![[Pasted image 20240707204012.png]]

Git enables full branching capability using directed acyclic graphs to store content. The history of a file is linked all the way up its directory structure (via nodes representing directories) to the root directory, which is then linked to a commit node. This commit node, in turn, can have one or more parents. This affords Git two properties that allow us to reason about history and content in more definite ways than the family of VCSs derived from RCS do, namely:

- When a content (i.e., file or directory) node in the graph has the same reference identity (the SHA in Git) as that in a different commit, the two nodes are guaranteed to contain the same content, allowing Git to short-circuit content diffing efficiently.
- When merging two branches we are merging the content of two nodes in a DAG. The DAG allows Git to "efficiently" (as compared to the RCS family of VCS) determine common ancestors.

### Distribution

### Toolkit

Git is a set of scripts basically, and is based on the Linux system command line tools.

The Git toolkit is divided in two parts: the *plumbing* and the *porcelain*
#### Plumbing

- Low level commands 
- Enable basic content tracking
- Manipulation of the DAG

#### Porcelain

- Commands that most Git end users are likely to need to use for maintaining repositories
- Commands for communicating between repositories for collaboration

## The Repository, Index and Working Areas

The `git init` command is the one in charge of starting or repository.

```bash
tree .git/
.git/
|-- HEAD
|-- config
|-- description
|-- hooks
|   |-- applypatch-msg.sample
|   |-- commit-msg.sample
|   |-- post-commit.sample
|   |-- post-receive.sample
|   |-- post-update.sample
|   |-- pre-applypatch.sample
|   |-- pre-commit.sample
|   |-- pre-rebase.sample
|   |-- prepare-commit-msg.sample
|   |-- update.sample
|-- info
|   |-- exclude
|-- objects
|   |-- info
|   |-- pack
|-- refs
    |-- heads
    |-- tags
```

We have a lot of directories and file, but we can have a little inspection on those to have a better idea of what they do

- Configuration: `/config`, `/description` and `/info/exclude` is to configurate the local repository
- Hooks: `/hooks` are scripts that can be run on certain lifecycle events
- Staging: `/index` will provide a staging are for our working directory.
- Object Database: `/objects` directory is the default Git object database, which contains all content or pointers to local content. They are **immutable** once created
- References:   the `.git/refs` directory is the default location for storing reference pointers for both local and remote branches, tags and heads. A reference is a pointer to an object, usually of type `tag` or `commit`. References are managed outside of the Object Database to allow the references to change where they point to as the repository evolves. Special cases of references may point to other references, e.g. `HEAD`

The `.git` directory is indeed the actual repository

The file of great importance is the `.git/index` file. It provides the staging area between the local working directory and the local repository 

The index is used to stage specific changes within one file (or more), to be committed all together. Even if you make changes related to various types of features, the commits can be made with like changes together, to more logically describe them in the commit message. To selectively stage specific changes in a file or set of files you can using `git add -p`.

### The Object Database

![[Pasted image 20240707210419.png]]

Git has four basic primitive objects that every type of content in the local repository is built around. Each object type has the following attributes: _type_, _size_ and _content_. The primitive object types are:

- _Tree_: an element in a tree can be another tree or a blob, when representing a content directory.
- _Blob_: a blob represents a file stored in the repository.
- _Commit_: a commit points to a tree representing the top-level directory for that commit as well as parent commits and standard attributes.
- _Tag_: a tag has a name and points to a commit at the point in the repository history that the tag represents.

All object primitives are referenced by a SHA, a 40-digit object identity, which has the following properties:

- If two objects are identical they will have the same SHA.
- if two objects are different they will have different SHAs.
- If an object was only copied partially or another form of data corruption occurred, recalculating the SHA of the current object will identify such corruption.

The first two properties of the SHA, relating to identity of the objects, is most useful in enabling Git's distributed model (the second goal of Git). The latter property enables some safeguards against corruption (the third goal of Git).

Despite the desirable results of using DAG-based storage for content storage and merge histories, for many repositories delta storage will be more space-efficient than using _loose_ DAG objects.

### Storage and Compression techniques

Git tackles the storage space problem by packing objects in a compressed format, using an index file which points to offsets to locate specific objects in the corresponding _packed_ file.

![[Pasted image 20240707212229.png]]

We can count the number of loose (or unpacked) objects in the local Git repository using `git count-objects`. Now we can have Git pack loose objects in the object database, remove loose objects already packed, and find redundant pack files with Git plumbing commands if desired.

The pack file format in Git has evolved, with the initial format storing CRC checksums for the pack file and index file in the index file itself. However, this meant there was the possibility of undetectable corruption in the compressed data since the repacking phase did not involve any further checks. 

Version 2 of the pack file format overcomes this problem by including the CRC checksums of each compressed object in the pack index file. Version 2 also allows packfiles larger than 4 GB, which the initial format did not support. As a way to quickly detect pack file corruption the end of the pack file contains a 20-byte SHA1 sum of the ordered list of all the SHAs in that file. The emphasis of the newer pack file format is on helping fulfill Git's second usability design goal of safeguarding against data corruption.

For remote communication Git calculates the commits and content that need to be sent over the wire to synchronize repositories (or just a branch), and generates the pack file format on the fly to send back using the desired protocol of the client.

### Merge Histories

As mentioned previously, Git differs fundamentally in merge history approach than the RCS family of VCSs. Subversion, for example, represents file or tree history in a linear progression; whatever has a higher revision number will supercede anything before it. Branching is not supported directly, only through an unenforced directory structure within the repository.

![[Pasted image 20240707214102.png]]

#### Limitations of Subversion (Linear-History VCS):

1. **Branch Work**: In Subversion, branches (e.g., `branches/branch-name`) represent parallel development to the trunk (main codebase).
2. **Merging Changes**: Merging changes from another branch into your working branch can be done manually, but Subversion doesn't track that these changes are included when merging into the trunk.
3. **Tracking Issues**: Subversion lacks a way to know which changesets from other branches are now in the trunk, making tracking changes across branches difficult.

#### Advantages of Git (DAG-Based Merge History VCS):

1. **Branch Work**: In Git, branches (e.g., `db-migration`) handle parallel development similar to Subversion.
2. **Merging Changes**: When merging changes from another branch, Git records the parent relationships of commits.
3. **Parent Relationships**: A commit in Git can have multiple parents, allowing it to track merges accurately using SHA hashes of parent commits.
4. **Merge Tracking**: Git knows the exact parent relationships and can track which branches' changes are included in the trunk (master) branch.
5. **Cherry-Picking**: For simpler cases, Git allows cherry-picking commits from one branch to another, applying a specific commit cleanly to the current branch.
#### Challenges in Both Systems:

1. **Commit Identification**: It's difficult to definitively know which commits are in each branch in both DAG-based and linear-based VCSs.
2. **Assumptions about Merges**: Assumptions about having merged all changes from both branches may not always hold true.

### Key Points

- **Subversion** struggles with tracking changes across branches after merging into the trunk.
- **Git** uses DAG-based commit history, which provides better tracking of changes with parent relationships and SHA hashes.
- **Cherry-Picking** in Git offers a way to handle simpler cases of applying specific commits between branches.
## Key points
	
- **Design Trade-offs**: Every design decision in software is a trade-off. Despite its benefits, Git has several common complaints due to its design choices.
    
- **Fondness for Git**: The author is a power user of Git and appreciates its current form, having developed software around the Git object database model.
    
- **IDE Integration**: One major complaint is Git's lack of IDE integration comparable to other VCS tools, due to its toolkit design.
    
- **Shell Script Commands**: Early Git commands were implemented as shell scripts, reducing portability, especially to Windows, which affected its adoption in larger organizations.
    
- **Git for Windows**: Volunteers started the Git for Windows project to ensure timely porting of new Git versions to Windows.
    
- **User Confusion**: Git's toolkit design and numerous plumbing commands often confuse new users, making adoption harder for some developer teams.
    
- **Future Development**: Despite these issues, there is excitement about the future development of the Git Core project and related open source projects.