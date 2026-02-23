# FCC Technical On-boarding Program


## 1. Introduction

**FCC Technical On-boarding Program** (**fTOP**)  is a structured technical training program run by the Tehran FCC Group. Its purpose is to build a core team of physicists and students who are proficient in the software, simulation, and data analysis tools used in modern experimental particle physics — specifically those relevant to the Future Circular Collider (FCC) project at CERN.

The program runs over two academic quarters (Q2 and Q3 of 2026) and is built around weekly sessions, hands-on tasks, and mandatory GitHub-based contribution tracking. It is not a lecture course. It is an apprenticeship: *participants are expected to read, build, break, fix, and contribute, not merely to listen.*

Upon successful completion, participants will have the practical skills to contribute directly to FCC analysis and simulation projects through our team's existing involvement in the collaboration.

## Strategic Context

The Tehran FCC Group holds Associate Member status at CERN and is actively involved in FCC software development and physics analysis. This is a meaningful position but its impact depends on the technical depth of the team behind it.

Currently, our team faces a structural gap: the number of members who are genuinely fluent in the HEP software ecosystem is insufficient for the scope of contributions we want to make. The tools required — ROOT, Geant4, Key4hep, FCCAnalyses, RooFit, and others — are not taught in standard physics programs. They must be learned through deliberate practice, ideally in an environment that connects learning to real work.

fTOP addresses this directly. It exists for three reasons:

**Reason 1 - Fill the internal gap.** We need people who can do analysis, simulation, and software development for our own FCC contributions. Without them, we are limited to tasks that don't require deep technical engagement.

**Reason 2 - Expand our contributions.** The FCC collaboration rewards teams that produce results. A technically capable cohort means more analyses, more simulation studies, more software contributions, and a more visible presence in the collaboration.

**Reason 3 - Build institutional weight.** A team with a track record of real technical contributions has a stronger voice in FCC affairs. fTOP is, in the long run, an investment in our team's influence and relevance within CERN.

---

## Program Philosophy

### Learning by doing

Reading documentation is necessary but not sufficient. Every phase of fTOP includes concrete tasks: running code, producing outputs, committing to GitHub, and presenting findings. If a participant cannot demonstrate that they have done something, it does not count.

### Teaching as learning

Participants are not passive recipients. Each member will be responsible for preparing and presenting at least one session, researching a topic in depth, and bringing that knowledge back to the group. This is how the program scales beyond a single lecturer, and it is how participants build the confidence to eventually work independently.

### Real stakes

This is not a study group. The skills developed here will be applied to real FCC projects. Participants should understand from the beginning that completing the program opens a direct path to contributing to CERN work. That is the motivation, and it should be taken seriously.

### Selective and small first

The first cohort is deliberately small and about five to eight people. This is not a public course. Quality of engagement matters far more than number of participants. A cohort of six committed people who all complete the program is worth more to the team than twenty who drift away by Phase 3.

---

## Eligibility and Selection

### Prerequisites

Applicants to the first cohort should have:

- Undergraduate-level knowledge of particle physics or a closely related field
- Working knowledge of at least one programming language (Python or C++ strongly preferred)
- Familiarity with basic Linux/command-line usage
- A genuine motivation to contribute to FCC work — not just to learn for its own sake

### Selection process (First Cohort)

The first cohort will be assembled through direct individual conversations, not open advertisement. Candidates will be drawn from:

- Current Tehran FCC Group members who have expressed interest
- Graduate and PhD students in the physics department with relevant backgrounds
- Exceptional final-year undergraduates in rare cases

There is no formal application form for the first cohort. Selection is based on a direct conversation with the program coordinator about background, motivation, and availability. The question being asked is simple: _Is this person ready to commit, and will they bring value to the group?_

### Commitment expected

Participants should expect to invest approximately **5 to 8 hours per week**: roughly 90 minutes for the weekly session, plus several hours for assigned tasks, reading, and GitHub contributions. Those who cannot make this commitment should not join the first cohort.

---

## Program Structure

### Weekly session format

Each week follows a consistent structure:

|Segment|Duration|Description|
|---|---|---|
|Presentation|45–60 min|One participant (or the coordinator) leads the session on the week's topic|
|Hands-on|20–30 min|Group works through a task or exercise together|
|Discussion & Q&A|10–15 min|Open questions, blockers, and planning for the week ahead|

### Alternating weeks

Phases with heavy practical components (ROOT, Geant4, Key4hep) will alternate between **lecture weeks** and **lab weeks**. In lab weeks, there is no new content — participants work through the previous week's exercises, debug together, and push their results to GitHub.

### Session ownership

Each session is owned by one participant, who is responsible for preparing the material, leading the presentation, and creating the corresponding GitHub entry (notes, code, exercises). Ownership rotates across the cohort. The coordinator guides, supplements, and ensures quality but does not do the work for the presenter.

## Curriculum Overview

The curriculum is organized into nine phases across two quarters.

### Q2 2026 (April – June): Foundations

|Phase|Topic|Approx. Duration|
|---|---|---|
|1|ROOT Framework and Core Tools|3 weeks|
|2|Statistical Methods for HEP|2 weeks|
|3|Python for HEP Analysis|2 weeks|
|4|Advanced Statistical Analysis: RooFit, RooStats, TMVA|3 weeks|

### Q3 2026 (July – September): Frameworks and Application

|Phase|Topic|Approx. Duration|
|---|---|---|
|5|Simulation Tools: Geant4 and Delphes|3 weeks|
|6|Event Data Models: EDM4hep, Podio, Gaudi|2 weeks|
|7|Key4hep and FCC Software Stack|3 weeks|
|8|Real Data: CERN Open Data and Experiment Frameworks|2 weeks|
|9|Community Practices, Advanced Topics, and Capstone|2 weeks|

---

## Phase Descriptions

### Phase 1 — ROOT Framework and Core Tools

ROOT is the foundational analysis framework of HEP. Virtually everything else in this curriculum depends on understanding it. Participants will learn to read and write ROOT files, create and manipulate histograms, perform fits, use TTree and RDataFrame, and write both C++ macros and Python scripts using PyROOT.

**Why it matters:** Every dataset in HEP is stored in ROOT format. Every analysis begins here.

**Key tools:** ROOT, CERN ROOT Tutorials, PyROOT

### Phase 2 — Statistical Methods for HEP

Particle physics is fundamentally a statistical science. This phase covers the core concepts: probability distributions, parameter estimation, hypothesis testing, confidence intervals, p-values, and the frequentist vs Bayesian distinction. Participants will work through problem sets and reproduce results from lecture materials.

**Why it matters:** You cannot claim a discovery or set a limit without understanding the statistics behind it.

**Key resources:** Glen Cowan's Statistical Data Analysis, Luca Lista's textbook
### Phase 3 — Python for HEP Analysis

Modern HEP analysis increasingly happens in Python. This phase covers the Python ecosystem specific to HEP: uproot for reading ROOT files without a ROOT installation, awkward-array for handling variable-length nested data structures, numpy and matplotlib for computation and visualization, and an introduction to the broader scikit-hep ecosystem.

**Why it matters:** FCCAnalyses and many modern analysis pipelines are Python-first. Proficiency here is directly required for FCC work.

**Key tools:** uproot, awkward-array, numpy, matplotlib, scikit-hep

### Phase 4 — Advanced Statistical Analysis: RooFit, RooStats, and TMVA

This phase moves from statistical concepts to their implementation in professional HEP tools. RooFit provides a framework for building and fitting probability density functions. RooStats extends this to hypothesis testing and limit setting. TMVA introduces multivariate analysis techniques — boosted decision trees, neural networks — within the ROOT ecosystem.

**Why it matters:** Signal/background discrimination and statistical inference are at the core of any physics analysis. These tools are used directly in FCC physics studies.

**Key tools:** RooFit, RooStats, TMVA (within ROOT), CMS Combine documentation as reference

### Phase 5 — Simulation Tools: Geant4 and Delphes

This phase introduces detector simulation at two levels. Geant4 is the full, detailed simulation framework used to model particle interactions with matter at the level of individual physics processes. Delphes is a fast parametric simulator that approximates detector response, enabling quick physics studies without the computational cost of full simulation.

**Why it matters:** Simulation is the backbone of any new experiment. FCC studies rely heavily on both Geant4-based full simulation and Delphes-based fast simulation.

**Key tools:** Geant4, Delphes, DD4hep (detector description)

### Phase 6 — Event Data Models: EDM4hep, Podio, and Gaudi

Modern HEP experiments use standardized data formats to ensure interoperability between simulation, reconstruction, and analysis software. This phase covers EDM4hep (the common event data model for FCC and other future experiments), Podio (the I/O layer), and the Gaudi framework (the algorithmic processing framework underlying Key4hep and ATLAS Athena).

**Why it matters:** FCC software is built on these standards. Understanding them is prerequisite to contributing to the FCC software stack.

**Key tools:** EDM4hep, Podio, Gaudi

### Phase 7 — Key4hep and FCC Software Stack

Key4hep is the unified software stack for future collider experiments, integrating Gaudi, EDM4hep, Podio, Geant4, and Delphes into a coherent framework. FCCAnalyses is the analysis framework built on top of Key4hep specifically for FCC physics studies. This phase is the most directly relevant to our team's FCC contributions.

**Why it matters:** This is the actual software our team uses and contributes to. Proficiency here translates directly into CERN contributions.

**Key tools:** Key4hep, k4FWCore, k4SimGeant4, FCCAnalyses, FCCSW


### Phase 8 — Real Data: CERN Open Data and Experiment Frameworks

Participants will work with real experimental data through the CERN Open Data portal, using CMS and ATLAS open datasets to perform actual analyses — including a re-creation of the Higgs boson discovery analysis. This phase also introduces the ATLAS Athena framework for context on experiment-specific software.

**Why it matters:** Working with real data exposes participants to the full complexity of actual analysis, beyond what any tutorial can simulate.

**Key tools:** CERN Open Data Portal, CMS open data tools, ATLAS xAOD, Athena (overview)

### Phase 9 — Community Practices, Advanced Topics, and Capstone

The final phase covers the professional and community dimension of HEP software: HSF training standards, software engineering practices for physicists, version control best practices, and an overview of advanced ROOT features (RDataFrame, TMVA SOFIE). The phase concludes with a capstone project in which each participant (or small group) produces a complete, documented, GitHub-hosted mini-analysis or simulation study.

**Why it matters:** Technical skills alone are not enough. Contributing to a collaboration requires working in a shared codebase, following community standards, and communicating results clearly.

## GitHub as the Backbone

All program activity is tracked through a dedicated GitHub repository hosted under the [HSQCD organization](https://github.com/hsqcd-collab). This is not optional; it is how contributions are measured and how the program maintains institutional memory.

### What goes on GitHub

- Session notes and summaries (in Markdown)
- All code written during sessions and as homework
- Exercise solutions and analysis outputs
- Each participant's learning log (a running personal Markdown document updated weekly)

### Contribution rules

- Every session generates at least one commit from the session owner
- Homework tasks must be submitted as pull requests and reviewed by at least one other participant
- Participants who go more than *three consecutive weeks* without a GitHub contribution are considered inactive

***GitHub contributions are verifiable, timestamped, and permanent. They serve as a portfolio of each participant's work — useful for future academic applications, job applications, and CERN collaboration involvement. A participant who completes fTOP with a rich GitHub history has something concrete to show for it. A participant who attended sessions but left no record did not really participate.***

---

## Roles and Responsibilities

### Program Coordinator

- Designs and maintains the overall curriculum
- Owns sessions where no participant is ready to lead
- Manages GitHub repository structure and contribution standards
- Liaises with CERN collaborators for guest lecture coordination
- Tracks participant progress and provides feedback

### Session Owner (rotating)

- Prepares material for their assigned session
- Leads the 45–60 minute presentation
- Creates the corresponding GitHub entry before the session
- Prepares at least two hands-on exercises for the group

### Participants

- Attend weekly sessions (two absences maximum per quarter with notice)
- Complete assigned exercises and commit to GitHub
- Prepare and own at least one session per quarter
- Review at least two pull requests per month from other participants
- Maintain their personal learning log

---

## Assessment and Progression

fTOP does not use grades. Assessment is based on observable outputs:

|Output|Expectation|
|---|---|
|GitHub contributions|Consistent, meaningful commits across all phases|
|Session ownership|At least one led session per quarter|
|Exercise completion|All assigned exercises attempted; most completed|
|Capstone project|A complete, documented mini-analysis or simulation study|
|Peer review|Active participation in reviewing others' pull requests|

At the end of Q2, the coordinator will have a brief individual conversation with each participant to assess progress and readiness for Q3. Participants who are significantly behind on GitHub contributions or exercise completion will be counselled on whether continuing is appropriate.

At the end of Q3, participants who have met the output expectations will be formally recognized as having completed fTOP and will be eligible for assignment to active FCC tasks through the team's collaboration projects.

---

## Guest Lectures and External Connections

Where possible, fTOP will invite specialists from the FCC collaboration to deliver sessions on topics they work on directly. These sessions are particularly valuable in the later phases (Key4hep, FCCAnalyses, FCC simulation) where first-hand operational knowledge is difficult to replicate from documentation alone.

Potential guest lecture formats include:

- A 60–90 minute walkthrough of a real analysis or simulation workflow
- A Q&A session with an FCC software or analysis expert
- A code review or feedback session on participant work

Connections for guest lectures will be developed primarily through the program coordinator's existing involvement in the FCC collaboration and through visits to CERN Geneva. Confirmed guest sessions will be announced to participants in advance.

## Timeline

|Period|Activity|
|---|---|
|March 2026|Cohort identification and individual conversations; GitHub repository setup|
|Late March 2026|Orientation session; program introduction; GitHub onboarding|
|April 2026|Phase 1 begins|
|April–June 2026|Q2: Phases 1–4|
|End of June 2026|Q2 check-in; participant progress review|
|July 2026|Phase 5 begins|
|July–September 2026|Q3: Phases 5–9|
|September 2026|Capstone projects; program completion|

---

## What Comes Next

Completing fTOP is the beginning, not the end. Participants who finish the program will be:

- Assigned to active FCC analysis or simulation tasks through the team's CERN involvement
- Eligible to co-author internal notes and contribute to published results
- Part of the core team that will eventually train the next cohort

The long-term vision is a self-sustaining technical team: people trained by fTOP become the next generation of session leaders, mentors, and contributors — gradually expanding the program and the team's capacity. The open education phase — where fTOP becomes available beyond the immediate team — will follow once the core cohort is established and the program format is proven.

_fTOP — Tehran FCC Group_  
_Program Coordinator: Amir H Ebrahimnezhad_
_Contact: [amir.ebh@cern.ch](mailto:amir.ebh@cern.ch)_  
_GitHub: [github.com/HSQCD-collab/fTOP]_