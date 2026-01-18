---
sticker: lucide//atom
---
#  Core Concepts
## Overview
In this document we would investigate Gradle 9.0.0 core concepts.
![[Pasted image 20250813180846.png]]
## Development
- **Projects**: A Gradle project is a piece of software that can be built, such as an application or a library. There are *Single project builds* which include a single project called the *root project*. Or *Multi project builds* which include one root project any any number of subprojects.
- **Build Scripts**: detail to Gradle what steps to take to build the project. Each project can include one or more builds scripts
- **Dependency Management**: is an automated technique for declaring and resolving external resources required by a project. Each project typically includes a number of dependencies that Gradle resolves  
- **Tasks**: are a basic unit of work such as compiling code or running your test. Each project contains one or more tasks defined inside a build script or a plugin.
- **Plugins**: are used to extend Gradle's capability. They optionally contribute tasks to a project.

