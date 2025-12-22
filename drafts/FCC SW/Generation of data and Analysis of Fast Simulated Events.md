# Introduction

The FCC software is fully embedded in the key4hep software stack, which means that the components providing the framework and those FCC specific are all available in key4hep. 

# Generators
## Overview
The Physics generators available for FCC usually come from key4hep. However, any generator able to generate events in one of the understood formats can be used in standalone. 

> A Good discussion: https://indico.cern.ch/event/1078675/
> On generators

the recommended formats are `HepMC3` and `EDM4hep`, `LHEf` is still much in use though. 

## Pythia8

`Pythia8` is fully integrated in `Key4hep` software stack and it provides diverse functionality in addition to event generation, including capability to read events in `LHEf` format.