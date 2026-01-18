---
sticker: lucide//atom
---
# Dependencies
## Overview
![[attch/Pasted image 20250815193622.png]]
Your application needs other libraries to be able to run, test, and build:
```kotlin
dependencies {  
    // Use JUnit Jupiter for testing.
    testImplementation(libs.junit.jupiter)

    testRuntimeOnly("org.junit.platform:junit-platform-launcher")

    // This dependency is used by the application.
    implementation(libs.guava)
}
```

## Development
Gradle automatically handles downloading, caching, and resolving these dependencies, saving you from managing them manually. It also handles version conflicts and supports flexible version declarations.

### Declaring Your Dependencies
To add a dependency to your project you simply specify it in the build script inside `dependencies {}`:

```kotlin
plugins {
    id("java-library")  
}

dependencies {
    implementation("com.google.guava:guava:32.1.2-jre") 
    api("org.apache.juneau:juneau-marshall:8.2.0")      
}
```

1. `id("java-library")`: Applies the Java Library plugin, which adds support for building Java libraries.
2. `implementation("com.google.guava:guava:32.1.2-jre")`: Adds a dependency on Google’s Guava library used in production code.
3. `api("org.apache.juneau:juneau-marshall:8.2.0")`: Adds a dependency on Apache’s Juneau Marshall library, used in library code.

Dependencies in Gradle are grouped by **configurations**, which define when and how the dependency is used:

- `implementation` is used for dependencies needed to compile and run your production code.
- `api` is used for dependencies that should be exposed to consumers of your library.


> [!NOTE] There are many other configurations available such as `testImplementation`, `runtimeOnly` and more.

### Viewing Project Dependencies
You can inspect the dependencies using the `dependencies` task:

```bash
./gradlew :app:dependencies
```

### Using a Version Catalog
A version catalog, let's you have all your dependencies regardless of where or with what configuration they are in one place, keeping track of dependencies, versions, can be hard. For this matter you can have a `gradle/libs.versions.toml` file. As an example.

This makes it easier to:
- Share common dependency declarations between subprojects
- Avoid duplication and version inconsistencies
- Enforce dependency and plugin versions across large projects
The version catalog typically contains four sections:
1. `[versions]` to declare the version numbers that plugins and libraries will reference.
2. `[libraries]` to define the libraries used in the build files.
3. `[bundles]` to define a set of dependencies.
4. `[plugins]` to define plugins.

Here's an example of a `libs.versions.toml` file:

```toml
[versions]
guava = "32.1.2-jre"
juneau = "8.2.0"

[libraries]
guava = { group = "com.google.guava", name = "guava", version.ref = "guava" }
juneau-marshall = { group = "org.apache.juneau", name = "juneau-marshall", version.ref = "juneau" }
```
Place this file in the `gradle/` directory of your project as `libs.versions.toml`. Gradle will pick it up automatically and expose its contents through the `libs` accessor in your build scripts. IDEs like IntelliJ and Android Studio will also pick up this metadata for code completion.

Once defined, you can reference these aliases directly in your build file:
```kotlin
dependencies {
    implementation(libs.guava)
    api(libs.juneau.marshall)
}
```
