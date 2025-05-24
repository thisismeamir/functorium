---
sticker: lucide//citrus
---
# The Functorium Method
*Categorical method of maintaining knowledge.*

## Overview
The **Functorium Method** is a categorical framework for managing knowledge, thoughts, projects, and research activity—particularly suited to polymaths and high-context, multi-domain thinkers. Inspired by category theory, Functorium models the evolution and interconnection of mental artifacts in an abstract yet precise architecture.

The method treats thoughts, cores, logs, and projects as objects in structured categories, using categorical concepts like morphisms, functors, and natural transformations (NaTTs) to represent relationships and dynamics.

## Introduction
Every Functorium starts with four categories:
1. Trace
2. Concept 
3. Theory
4. Scheme

### Trace
Trace are the raw stream of consciousness, reflections, or activity records written each day. They prioritize **low-friction documentation** over structure. 

A polymath, who works on different subjects, projects, and activities. There's not necessarily a peaceful time to write structured documents at first glance. That's why our journey starts by writing logs (traces). Single purpose documents that would be written each day, on different topics, matters, thoughts, or tasks. This would help the person quickly start documenting, without the need to be very disciplined about the document that they write.

These documents are for efficiency and documentation purposes only, they are not to be printed out, shared. At the end of each week we re-base them in new files; making them clear by separating the document into thoughts, lectures, knowledge, projects, and other types.
#### Properties:
- Atomic and unsorted.
- One document per day, split across topics or ideas.
- **Not shareable or polished.**

#### Weekly Rebase:
Each week, logs are "rebased" into cleaner categories:
- **Concept** (for ideas and insights)
- **Theory** (for structured learnings)
- **Scheme** (for tangible goals))

Logs are considered their own atom type: **Log atoms**.
#### Morphisms in Logs:
- `Chronological`: links traces by date
- `Annotation`: attaches traces or references

### Concept
A thought, idea, or aha moment, is important in the mind of a poly math, its a concept that came to mind, a thing that can be investigated, and processed, we separate this into two main areas, `Postulates` and `Threads`. 

Concept must hold the mental phenomena like insights, investigations, and cognitive threads.

#### Postulate
A Postulate is a unit of thought in Functorium. These are atomic and messy insights, and therefore, there's no obligation for structure. These are about when something clicks. A postulate can be about anything, but it should be very clear what exactly that thing is. It cannot be blob of information, it should be written in a way that it can be investigated through time. 



#### Thread
We think about many postulates during a day, but some of the times, these postulates are sequential. Threads are the means of providing a structured or semi-structured sequence of postulates. It helps tracking the development over time and Often leads to Theory atoms or Scheme objectives.

#### Morphisms in Concept
- `Refinement`: $\text{postulate}\rightarrow\text{thread}$.
- `Connection`: Links disparate ideas.
- `Abstraction`: Generalizes a Thread into a broader Principle.

$$
\text{Thread} := x_1 \rightarrow \dots \rightarrow x_n  \ \ \text{where} \ x_i\in\text{Postulates}
$$

### Theory
Theories are what is explicitly learned, formalized or composed. They are what makes up our knowledge. These can be gathered by lectured, discussions, workshops, or readings. We start off by having a structured way of maintaining them, while an important part is to keep our model consistent and with less misinformation getting in.
#### Atom
Atoms are single statements of knowledge, they are meant to be short reading materials to learn a single concept with the least amount of context, by this we mean that we should not read 3 other atoms to learn one. Or at least in principle we should maintain near to zero amount of atoms related to one another. Atoms are by definition atomic forms of knowledge (e.g a theorem, definition, or derived result).

#### Models
A Model is a sequence of atoms that aims to provide content for a more complex statement of knowledge. These explain or develop a concept that needs context. 

Generally speaking a model is a diagram:
$$
A_0\rightarrow \dots\rightarrow A_n
$$
where $A_i\in \text{Atoms}$.
#### Morphisms in Theory
- `Dependency`: $A\rightarrow A'$ to understand $A$, you need to know $A'$ .
- `Inclusion`: $\text{Atom}\in\text{Model}$ 
- `Refinement`: $A\rightarrow  A^*$. Replacement of an atom with a more precise one.
- `Equivalence`: Atoms express the same idea differently.

### Schemes
Schemes are simply projects, they contain goals, and process indicators, as well as progress evaluation. These are structured units of intention, and execution. Schemes are structured units of intention and execution. Unlike Concepts or Theories, Schemes are **teleological**: they have goals, constraints, and internal processes.

**Properties**:
- Not atomic
- Built from and interacts with Thoughts and Knowledge
- Has its own internal structure: **Objectives**, **Processes**, and **Steps**
- Evolves across time, potentially influencing new Models or Threads

Schemes are not just applications—they’re **living systems** with their own logic. They use insights (Threads), formal results (Atoms), and may generate their own artifacts in form of threads, and atoms as well out external ones (codes, papers, publishing and other)
#### Objectives
An objective is a goal, something that should happen within a time-span. They are usually by-products of threads. 

#### Entropy 
Systems or workflows to reach those objectives
#### Morphisms in Schemes
- `Milestone`: $P \rightarrow P′$ (progress or phase transition)
- `Requirement`: $\text{Atom}\rightarrow P$ (uses a piece of formal knowledge)
- `Reference`: $\text{Thread or Model}\rightarrow P$  (conceptual or theoretical grounding)
- `Decomposition`: $P → \{P_1, P_2, \dots, P_n\}$ (splitting into subprojects)
- `Generation`: $P \rightarrow \text{Postulate, Atom}$ (Schemes create new Postulates or Atoms)

## Natural Transformations in the Functorium

In the architecture of the Functorium, the central structures are Categories such as Traces, Concepts, Theories, and Schemes. These are interconnected through morphisms and functors that enable the transformation of one mental structure into another, preserving their internal logical or procedural relationships. Up to this point, functors have served as the scaffolding for building coherent knowledge pathways. Natural transformations now enter the scene as a higher-order connective tissue: they mediate between functors themselves.

---

### What is a Natural Transformation?

Given two functors $F, G: \mathcal{C} \rightarrow \mathcal{D}$, a natural transformation $\eta: F \Rightarrow G$ is a structured collection of morphisms $\eta_X: F(X) \rightarrow G(X)$ for each object $X$ in $\mathcal{C}$, such that for every morphism $f: X \rightarrow Y$ in $\mathcal{C}$, the following diagram commutes:

$$\begin{aligned} F(X) & \xrightarrow{F(f)} F(Y) \\ \downarrow^{\eta_X} & \quad \downarrow^{\eta_Y} \\ G(X) & \xrightarrow{G(f)} G(Y) \end{aligned}
$$
This formalism ensures that the transformation from functor F to G is coherent with the structure of morphisms in $\mathcal{C}$. One may think of it as a "bridge" between two interpretative or generative systems.

---

### Natural Transformations as Epistemic Equivalences

In the Functorium, functors represent cognitive strategies or construction pathways from one type of mental object to another: a functor from Concepts to Theories may encapsulate a methodology for converting loose ideas into rigorous frameworks.

A natural transformation $\eta: F \Rightarrow G$ between two such functors represents a _systematic equivalence between two knowledge-generation strategies_. The emphasis is not just on mapping outputs, but on preserving the internal logic of development:

- If $F$ maps a concept to a theoretical formulation through mathematical formalization, and $G$ does so through simulation and modeling, $\eta$ gives a way to interpret the mathematical results in terms of the simulation (and vice versa), for every concept processed.
    
- The commutativity condition ensures that knowledge paths (threads, refinements, generalizations) developed under $F$ can be transported to $G$ without conceptual incoherence.
    

This structure is particularly powerful when comparing paradigms, dialectics, or schools of thought.

---

### 3. Practical Manifestations in the System

#### a. Translation of Threads

Suppose FF and GG are functors from Traces to Concepts, each encoding a way of interpreting raw thoughts (traces) into coherent concepts. A natural transformation between them would allow one to take a trace interpreted through one lens (say, phenomenological) and reinterpret it under another (say, analytical), while respecting the process by which the trace was formed and related to others.

#### b. Project Workflows

Given two functors from Schemes to Theories, representing different workflows or research methodologies, a natural transformation organizes a "project translation layer." It enables consistent switching between perspectives, such as from a theoretical research design to an applied prototyping model.

#### c. Educational Layering

Functors that map Concepts to Learning Modules or Curriculum Theories can be naturally transformed to one another. For instance, a mathematically rigorous curriculum and a visual-intuitive one may both be functorial maps from a shared conceptual base. The natural transformation would organize how lessons in one pedagogy correspond to another.

---

### 4. Cognitive Significance

Where functors encode _epistemic strategies_, natural transformations represent _meta-cognitive bridges_. They let us move between different approaches to knowledge without collapsing the internal rationale of each. In this sense, a natural transformation is not just a structural mapping, but a principle of _cognitive coherence_ between differing paradigms. They ensure that intellectual development retains identity even when translated.

This is not only philosophically satisfying; it is practically crucial in interdisciplinary research, multi-perspective modeling, and any system of thought where pluralism and translation are necessities.

---

### 5. Future Directions: Higher Transformations

Just as natural transformations relate functors, one may consider **modifications** (morphisms between natural transformations) and eventually move toward the construction of a full **2-category** of knowledge. This opens the path for organizing transformations of transformations, offering new ways to manage revision, metatheory, or self-reflection in a structured way.

In the long-term vision of the Functorium, such higher-level coherence mechanisms will form the core of the _reflective layer_ of knowledge architectures: a domain where thought is not only produced, but also transformed, compared, and harmonized across dimensions.

