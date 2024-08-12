Keywords: #CI #process #Infra #DevOps

This are systems that **build** and **test** software ***automatically and regularly***

They also can be used for other tedious tasks, not just test and build, many of the uses are:

- Cross-platform testing
- Regular running of slow, data-intensive, or difficult-to-configure tets
- Verification of project performance
- Failing test detection

This usually the first step to have, to move  to ***Continuous Deployment***

In this lecture we are going to discuss 4 tools:

- Buildbot: Master/slave system
- CDash: Reporting server model
- Jenkins: Hybrid model
- Pony Build: Decentralized reporting server based on Python

## Landscape

The main architecture are: master/slave and reporting architectures.

>[!IMPORTANT]
>master/slave is a type of software architecture, in which a central server directs and controls remote builds

>[!IMPORTANT]
> reporting architectures is those in which a central server aggregates build reports build reports contributed by clients

One example of master/slave (centralized) could be **Buildbot**, which is baswed on two components:
- buildmaster or server: Which schedule and coordinates builds between one or more connected clients
- buildslaves or clients: Which execute those builds

Basically, the buildmaster sends all the neccesary information to the buildslaves (steps, secrets, who is the buildmaster), the master sends the task and the slave prints out

One example of reporting is **CDash**, which is used for the VTK/ITK projects by Kitware. One clients runs the reporting and after finishes, this is send to CDash server to store it.

A combination of bots is **Jenkins** (or Hudson before 2011), these builds can be executed independently and sent back to the master or can be scheduled by a master.

## What CI tools do?

***Build, run tests and report the results***

All those tasks can be done with just a script running on those machines (with task or cron-jobs) 

![[Pasted image 20240811191304.png]]

But this is simple, most of the real world CI systems do more things 

- **Checkout and Update**: Updating an existing codebase is more efficient than checking out a new copy, saving bandwidth and time. CI systems track and update the working copy in place, requiring basic VCS integration.
    
- **Abstract Build Recipes**: Build recipes vary by OS (e.g., Mac vs. Windows). CI systems need to either create specialized recipes or provide an abstraction layer to handle these differences.
    
- **Storing Status**: CI systems should store details on checkouts, builds, and tests for later analysis. This helps answer questions about performance and code coverage across architectures and over time.
    
- **Release Packages**: Builds often produce binary packages that need to be made accessible to developers. CI systems should manage transferring these products to a central repository.
    
- **Multiple Architecture Builds**: CI systems should track w hich architecture each build targets and link build outcomes to specific machines to support cross-platform testing.
    
- **Resource Management**: CI systems may need to manage resources by scheduling builds based on machine availability and resource load to avoid overloading.
    
- **External Resource Coordination**: Integration tests often need external resources like staging databases. CI systems should coordinate access to these resources across multiple machines.
    
- **Progress Reports**: For long builds, regular progress updates are crucial to avoid making users wait until the end to see initial results'

### Interactions

1. **Build Notification**: Communicate build outcomes to interested parties via pull (e.g., web, RSS) or push methods (e.g., email, Twitter). Notifications can cover all builds, only failures, or builds not executed in a set period.
    
2. **Build Information**: Retrieve build details and products through RPC or bulk download. This includes accessing in-depth analyses, code coverage, and performance results. External repositories may track test results separately from the CI system.
    
3. **Build Requests**: Handle external build requests from users or version control systems (VCS). This can be through post-commit hooks or manual requests via web interfaces.
    
4. **Remote Control**: Manage the CI system via RPC to modify runtime settings, drive builds on specific platforms, and handle various branches or conditions. This supports flexible workflows and integration with external systems, like bug trackers and patch systems.

## Architecture

### Buildbot

![[Pasted image 20240811191848.png]]


The remote execution is entirely scripted by the master server in real time: the master configuration specifies the command to be executed on each remote system, and runs them when each previous command is finished

Buildbot mantains a constant connection with teach buildslave, and coordinates job exeution between them. This feature adds ***a lot of complexity*** , for example:

- Testing is hard
- Keep the connection is hard
- OS alert windows are difficult to deal with

Thanks to that tight control, the build coordination between resources is **very easy**

>[!IMPORTANT]
>Adding complexity maybe is worth it, to gain speed in another aspects.

This also have lock restrictions for both slave and master, so that builds can coordinate system-global and machine local resources.

The use of centralized configuration can bring a lot of issues for distributed models. But this can be avoided with some configuration, BUT, the clients are vulnerable to misconfigurations and malicious configurations

>[!IMPORTANT]
>The client must have OS security

Other issue with this architecture, is the low level of communication, for example, **buildslaves do not report system utilization and the master cannot be configured to be aware of high slave load**.,

External CPU notification of build results is handled entirely by the buildmaster, and new notification services need to be implemented within the buildmaster itself. Likewise, new build requests must be communicated directly to the buildmaster.

### CDash

![[Pasted image 20240811195903.png]]

Here are the key points about CDash and its model:

- **Reporting Server Model**: CDash uses a reporting server model where the CDash server acts as a central repository for build information, including build and test failures, code coverage, and memory usage.
- **Build Reporting**: Builds are executed on remote clients on their own schedule and submit reports in XML format.
- **Client and Non-Core Developers**: Both official build clients and non-core developers or users running the build process on their own machines can submit build reports.
- **Integration with Kitware Infrastructure**: CDash integrates closely with CMake (build configuration), CTest (test runner), and CPack (packaging system), providing a high-level, OS-agnostic approach to build, test, and packaging recipes.
- **Client-Driven Process**: Clients decide when to run builds based on their own conditions (e.g., time of day, load) and can easily participate in volunteer or cloud builds.
- **Build Uploads**: Build products are sent to the central server via a straightforward upload mechanism.
- **Lack of Centralized Coordination**: CDash does not offer centralized resource coordination, progress reports, or guaranteed response from anonymous clients.
- **CDash @Home**: Introduced a cloud build system where clients offer build services to the CDash server, poll for build requests, and return results.
- **Manual Build Requests**: As of October 2010, builds must be manually requested on the server, and clients need to be connected to offer services.
- **Future Enhancements**: Potential to extend the "@Home" system to automatically schedule builds based on client availability, similar to the Pony-Build system.

### Jenkins

- **Deployment Flexibility**: Jenkins can function as a standalone CI system, a coordinator for remote builds, or a passive receiver of remote build information.
- **Reporting Standards**: Utilizes the JUnit XML standard for unit test and code coverage reporting, integrating reports from various test tools.
- **Hybrid Operation**: Operates in a hybrid mode with default master-server build execution, but supports remote builds via server- and client-initiated methods.
- **Remote Machine Management**: Manages multiple remote machines through SSH connections or JNLP (Java Web Start), supporting two-way communication for object and data transfer.
- **Plugin Architecture**: Features a robust plugin architecture that abstracts connection details, enabling the development of third-party plugins for additional functionalities like returning binary builds and more comprehensive result data.
- **Locks Plugin**: Includes a "locks" plugin to prevent parallel job execution controlled by the central server, although it was not fully developed as of January 2011.

### Pony Build

![[Pasted image 20240811200058.png]]

- **Decentralized CI System**: Pony-Build is a proof-of-concept decentralized CI system written in Python.
    
- **Core Components**:
    
    - **Results Server**: Centralized database containing build results from individual clients.
    - **Clients**: Contain configuration information and build context; include a lightweight library for VCS access, build management, and result communication.
    - **Reporting Server (Optional)**: Provides a Web interface for build results reporting and build requests; can run separately from the results server.
- **Communication and Notification**:
    
    - **Webhooks and RPC**: Used for build and change notifications, and build introspection.
    - **PuSH Protocol**: For active notification of new or failed builds, allowing integration with various applications.
- **Advantages**:
    
    - **Ease of Communication**: Simple to implement using basic web programming knowledge.
    - **Easy Modification**: Adding new notification methods or reporting interfaces is straightforward.
    - **Multiple Language Support**: Components can be implemented in different languages due to webhooks.
    - **Testability**: Components can be isolated and mocked for testing.
    - **Ease of Configuration**: Minimal client-side requirements, with only one library file needed.
    - **Minimal Server Load**: Central server handles only reporting, not client control, reducing load.
    - **VCS Integration**: Build configuration is client-side and included within the VCS.
    - **Ease of Results Access**: Results can be accessed through XML-RPC requests, and clients only need to post results to the server.
- **Disadvantages**:
    
    - **Difficulty Requesting Builds**: High load and latency due to clients polling the server or needing complex command/control connections.
    - **Poor Support for Resource Locking**: Challenges in enforcing client policies and handling client failures or deadlocks.
    - **Poor Support for Real-Time Monitoring**: Difficult to implement real-time monitoring and control due to lack of constant connection. Intermediate build inspection and interruption are challenging.
    - **Implementation of Recipes and Trust Management**: Issues with executing arbitrary code on build clients and managing trust between clients and the CI system.

## Build Recipes

- **Purpose**: Build recipes provide abstraction for building, testing, and packaging software, especially across multiple platforms.
- **CDash Example**: Relies on tools like CMake, CTest, and CPack to handle multi-platform issues.
- **Python Ecosystem**: Lacks a standard for test discovery and results collation; distutils and distutils2 are used for building and packaging but with variations.
- **Challenges**: Recipes need to be platform-independent and customizable to the software being built.

## Trust

- **Trust Issues**: The CI system must trust both the software and the build recipes since recipes execute arbitrary code.
- **Controlled Environments**: Easier to manage trust within a company or internal process.
- **Open Source and Community Builds**: Ideal to support standard recipes or digitally signed recipes to manage trust for external build services.

## Choosing a Model

- **Loosely Coupled Models**: Easier to implement with RPC or webhook callbacks; flexible, expandable, and easier to test and modify.
- **Build Coordination**: Challenging in loosely coupled models, involving difficulties in starting/stopping builds and coordinating resource locks.
- **Decision Factors**: Choice of model should align with the project's needs, considering whether tight build coordination is necessary.

## The Future

- **Language-Agnostic Recipes**: Desire for a universal build configuration language to simplify CI across various systems.
- **Common Reporting Formats**: Standard formats for build and test reporting to enable easier integration and summary views.
- **Granularity and Introspection**: API access for detailed build information rather than relying on common formats alone.

## Concluding Thoughts

- **Architecture and Features**: Architecture influences the features of CI systems; for instance, Pony-Build's choice of a reporting architecture affected its design and feature set.
- **Feature Set and Architecture**: Systems like Buildbot, CDash, and Jenkins are tailored to specific use cases and feature sets based on their architecture.
- **Open Source Sociology**: Contributors may favor projects whose architecture fits their needs, leading to feature lock-in.
- **Evolution of CI Systems**: CI systems are expected to evolve with additional features as they mature, but the base architecture may constrain their development.