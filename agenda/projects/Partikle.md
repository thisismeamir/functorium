Partikle project is essentially a framework/interface for experimental/computational particle physics. It aims to provide a unified landscape for pipelines of simulation, detectors, numerical evaluation and other fields in experimental particle physics.

The core idea is to build an ecosystem that relies on foundational software, but at the same time, provides clean, physics-oriented, language to work with in analysis and experimentation.

Partikle is going to be built on two main languages, a C++ core which acts as the bridge between previous software and provides fast, low-latency computations. And a Kotlin front-face, which because of its expressiveness would allow researchers to develop and analyze at faster phases. 

With the use of rich type system of Kotlin, Partikle aims to be accurate in terms of dimensions, units, quantities and physical descriptions. As an example numbers in Partikle would be represented with their respective dimension/unit:

```kotlin
val x = 2.m // 2 Meters
val y = 3.GeV 

// x + y would raise a type error as they are fundamentally different numbers.
```

Another key factor of Partikle is a rich expressiveness as an outcome, instead of relying of different DSLs when working between frameworks and libraries. Partikle provides a unified interface and handles the necessary conversions behind the scene:

```kotlin
val simulation =  Simulation {
	val beam = beamOf(Electron)
	  .withEnergies { 10.GeV }
	val detector = CLCD
}
```