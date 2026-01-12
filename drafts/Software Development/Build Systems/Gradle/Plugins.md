---
sticker: lucide//atom
---
# Plugins
![[Pasted image 20250815194243.png]]
## Overview
Plugins extend the capabilities of Gradle, adding a plugin to a build script is called *applying* the plugin.
```kotlin
plugins {
	application
}
```
The `application` plugin[^1] facilitates creating and executable JVM application. 

## Use Convention Properties
Gradle is built on a flexible plugin system.
Out of the box, Gradle provides core infrastructure like dependency resolution, task orchestration, and incremental builds. Most functionality — like compiling Java, building Android apps, or publishing artifacts — comes from **plugins**.

## What is a plugins
A plugin is a reusable piece of software that **provides additional functionality to the Gradle build system**. It can:

- Add new tasks to your build (like `compileJava` or `test`)
- Add new configurations (like `implementation` or `runtimeOnly`)
- Contribute DSL elements (like `application {}` or `publishing {}`)

Plugins are applied to build scripts using the `plugins` block (Kotlin DSL or Groovy DSL), and they bring in all the logic needed for a specific domain or workflow.

## Applying a Plugin
Plugins can be applied inside a build scripts using the `plugins {}` block, 
```kotlin
plugins {
    id("«plugin id»").version("«plugin version»")
}
```
For example 
```kotlin
plugins {
	id("java-library")
	id("com.diffplug.spotless").version("6.15.0")
}
```


This tells Gradle to:
- Apply the built-in `java-library` plugin, which adds tasks for compiling Java, running tests, and packaging libraries.
- Apply the community-maintained `spotless` plugin (version `6.25.0`), which adds code formatting tasks and integrates tools like `ktlint`, `prettier`, and `google-java-format`.

## Plugin Types

Gradle supports three types of plugins:
1. **Script plugins** – Reusable `.gradle` or `.gradle.kts` files that are applied using `apply from:`.
2. **Pre-compiled plugins** – Packaged Kotlin or Groovy code applied with the `plugins {}` block.
3. **Binary plugins** – Packaged and published plugins (often from the Plugin Portal or Maven) that are applied with the `plugins {}` block.

Most modern builds prefer **binary** or **precompiled** plugins.

## Morphisms
- Depends on
- Is included in
- Refined by
- Is Equivalence to

## Tags
#atom #theory 

[^1]: [[Gradle Application Plugin]]
