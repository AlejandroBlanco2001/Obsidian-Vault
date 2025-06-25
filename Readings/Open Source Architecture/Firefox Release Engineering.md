---
tags:
  - release
  - process
  - OpenSourceArch
---
Mozilla had troubles with process in a very manual way, in this order of ideas, they had a major issue regarding human errors in multiple possible scenarios, for example, what if during a sanity check the QA forget to test something? What make one release per platform?

For this reason, they decide to automate as much as possible, document everything, communicate everything and keep everyone on the same page.

# Look _N_ Ways Before You Start a Release

![[Pasted image 20240803011928.png]]

They set some premises to put some order in their release mindset:

1. the more popular Firefox became, the more users we would have
2. the more attractive a target Firefox would become to blackhat hackers looking for security vulnerabilities to exploit
3.  the more popular Firefox became, the more users we would have to protect from a newly discovered security vulnerability

Following this idea, there is a need to deploy security fixes, fast , really fast. Therefore, the mindset has changed

> What if instead of thinking that a regular release would need an emergency hotfix and be a hotfix release, what if we think that every release is a hotfix release.

So, to have a better understanding of the process, they had three ideas:

1. Every release, must have a postmortem file, to know to see where things could be made smoother, easier, and faster next time. Goal is to have less human interaction
2. When we do have a chemspill release, the more robust the release automation, the less stressed the humans in Release Engineering are. We're used to the idea of going as fast as possible with calm precision, and we've built tools to do this as safely and robustly as we know how.
3. Mozilla now has a full-time person to track the readiness of the code for a "go to build" decision. Changing processes during a chemspill is risky, so in order to make sure everyone is familiar with the process when minutes matter, we use this same process for chemspill and regular releases.

![[Pasted image 20240803012745.png]]

## Go to Build
