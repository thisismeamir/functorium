
# Simulation Based Inference

## Part I General View 

In this part we are going to work through a general view of simulation based inference.
There's a large number of objects and orders of magnitude that constructs our territory. 

### Roadmap, Motivation, and Terminology

The roadmap of data modeling consists 
1. Scientific methodology
2. model building
3. data modeling
4. summary statistics and field-level
5. simulation-based inefrence


Our terminology consists of:
1. Physics as Basic Science
2. Scientific method and methodology
3. Theory
4. Simulation
5. Data modeling
6. Measurement and Error Analysis
7. Experiments
8. Parameter Constraining
9. Summary Statistics
10. FieldLevel inference
11. Simulation based inference

What is a reseach?
Looking to answer: What, Why and How questions
Research is done with the help of study, experiment, observation, analysis.
Research methods are the various procedures, schemes, and algorithms used in a research.
What is research methodology?
Research methodology is a systematic way to solve a problem
- it is the science of studuing how reearch is to be carried out
- Its objective is to give the work plan of research 
For example: Investigation of electrical conductivity, in this example what is the method and what is methodology

Methodology deals with 
- doing experiment simulation and why?
- In experiment, setting up the thermodynamics or electrucuty tools
While method deals with
- How to use an Ampere-meter?
- How to measure the electric current?
- How to compute the Resistivity from collected data set?

In out scientific methodology there are three pillars:

- We've got theory which is based on first principles, phenomenology and effective theory.
- Experiment
- A way to connect the two (which is the place where summary statistice and field-level inference comes to play)
	- Starts with data modeling, bayesian inference, frequentism, model-based, data-based, etc
	- Simulation
		- Simulation gives feedback on experiment and on theory making it a vital tool for doing physics. Specially since it costs a lot less than experimenting
		- Also sometimes simulation is wrong which shows us some implemention of theory


The main question sometimes are the what is the probability of obtaining parameters values given observations.


#### Parameters
Models most of the time contain constants and parameters that need to be specified through experiment. But then we need to compare Observations/Experiments with Theory, this is the main goal of data modeling. A way to connect numbers of an experiment with mathematical constructs. 

Data modeling: Theory based
- Measurement and observation
- Error evaluation
- Model selection
- Free parameters
- Confidence interval
- Evidence and Goodness of fit

There are two challenges here:
1. A priori-that's it, so model is vital and by each model we have to go through this cycle.
	1. A solution to this is Bayesian model averaging
2. The second challenge is what should we do it there is no explicit relationship between parameters and observations?
	1. Hwo to compare theory with experiment if there's no easy way to find the relation between the observed parameter and the theoretical parameters.
	2. This is the interactable likelihood, and one of our main reasons to do simulation based inference.

Data modeling: Data based
- Measurement and observation
	- Morphology
- Error evaluation
- Model selection
	- BMA
- EMulator
- Free parameters
- Confidence interval
- Evidence and Goodness of fit

The main question to answer in data modeling

The main question is How consistent is a given model with experiment? Finding the probability of obtaining parameter values given observation, maximizing the posterior function.

### Bayesin Theorem

$$
P(\Theta, \mathcal D) = \frac{\mathcal L(\mathcal D|\Theta)P(\Theta)}{P(\mathcal D)}
$$

and $P(\mathcal D)= \int d\Theta\mathcal L(\mathcal D | \Theta) P(\Theta)$

where $P(\mathcal D)$ is the evidence.

At best we want to maximize $P(\Theta|\mathcal D)$, 

# Summary Statisticss

1. We have a generic theory
2. A set of model's free parameters $\{\Theta\}$
3. Compressing data into a few summary numbers.
	- This approach has pros and cons

For example there are traidtional summary statistics
- Background
- Perturbations
	- Structure formation
	- Spectrums
	- Lensinz
	- SZ-effect
New summary statistics
- Topology
- Geometry
- Graph

# Field-Level

The goal is to directly use the raw data for physical inferences.