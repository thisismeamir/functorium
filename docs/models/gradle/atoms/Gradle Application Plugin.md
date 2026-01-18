---
sticker: lucide//atom
---
# Gradle Application Plugin
## Overview
The `application` plugin facilitates building an executable JVM application.
## Development
The `application` plugin defines tasks that package and distribute an application, such as the `run` task. The Application plugin provides a way to declare the main class of a Java application, which is required to execute the code.
```kotlin
application {   
    // Define the main class for the application.
    mainClass = "org.example.App"
}
```
 

In this example, the main class (i.e., the point where the program’s execution begins) is `org.example.App`.
