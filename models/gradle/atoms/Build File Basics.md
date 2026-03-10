---
sticker: lucide//atom
---
# Build File Basics
## Overview
Generally a build script, details tasks and plugins to build a sub-project.
![[../../../attachments/Pasted image 20250813190659.png]]

> [!DANGER] Every Gradle project should at least have one `build.gradle` file. Usually to be found in the root folder.

## Development
### What To Find in a Build Script?
In a Build script one usually finds:
1. **Plugins**: Tools that let you extend Gradle functionality for running tasks and builds.
2. **Dependencies**: Libraries and tools your project uses.

Specifically build scripts contain two types of dependencies:
1. **Gradle and Build Script Dependencies**: These include plugins and libraries required by Gradle itself or the build script logic.
2. **Project Dependencies**: Libraries required directly by your project’s source code to compile and run correctly. 

As an example:
```kotlin
plugins {   
    // Apply the application plugin to add support for building a CLI application in Java.
    application
}
dependencies {  
    // Use JUnit Jupiter for testing.
    testImplementation(libs.junit.jupiter)

    testRuntimeOnly("org.junit.platform:junit-platform-launcher")

    // This dependency is used by the application.
    implementation(libs.guava)
}
application {   
    // Define the main class for the application.
    mainClass = "org.example.App"
}
```
1. `plugins`: Used to introduce plugins
2. `dependencies`: Used to declare dependencies of the project.
3. `application`: Used for introducing convention properties

Build scripts are evaluated during the configuration phase of a build, and they serve as the main entry point for defining a (sub)project’s build logic. In addition to applying plugins and setting convention properties, build scripts can:
- Declare dependencies
- Configure tasks
- Reference shared settings (from version catalogs or convention plugins)
