# Two-Year Mobility Grant Proposal

**Programme:** Indo-Austrian S&T Cooperation – Project-Based Personnel Exchange (BMWFW / DST)

**Project Title:** Evolutionary Algorithms for Quantum Circuit Optimization and Noise-Resilient Variational Algorithms on NISQ Hardware

---

## Applicant Details

| | Austrian Side | Indian Side |
|---|---|---|
| **Principal Investigator** | Prof. Dr. Michael Affenzeller | Dr. Anupam Yadav |
| **Institution** | University of Applied Sciences Upper Austria (FH OÖ), Hagenberg Campus – HEAL Lab | National Institute of Technology Jalandhar (NIT Jalandhar), Department of Mathematics |
| **Address** | Softwarepark 11, 4232 Hagenberg, Austria | G.T. Road, Amritsar Bypass, Jalandhar – 144 027, Punjab, India |
| **Email / URL** | michael.affenzeller@fh-hagenberg.at / https://heal.heuristiclab.com/team/affenzeller | anupam@nitj.ac.in / https://departments.nitj.ac.in/dept/ma/Faculty/6430446b38bff038a7808524 |
| **Duration** | 24 months | 24 months |

---

## Abstract

Quantum computing on Noisy Intermediate-Scale Quantum (NISQ) hardware suffers from two fundamental bottlenecks: the absence of scalable, noise-aware methods for designing and compiling quantum circuits, and the lack of principled multi-objective frameworks that jointly optimise circuit fidelity, depth, and hardware noise sensitivity. Evolutionary Algorithms (EAs)—in particular, multi-objective genetic algorithms, genetic programming, CMA-ES, and surrogate-assisted variants—are uniquely suited to address these bottlenecks because they operate gradient-free, handle mixed discrete-continuous search spaces natively, and support Pareto-based multi-objective optimisation. Yet the systematic application of advanced EA methodology to quantum circuit design, variational quantum eigensolvers (VQE), and noise-aware pulse optimisation remains at an early stage, with critical gaps in surrogate assistance, multi-objective formulations, and scalability.

This two-year Indo-Austrian mobility project brings together the Heuristic and Evolutionary Algorithms Laboratory (HEAL) at FH OÖ Hagenberg—one of Europe's leading groups in evolutionary computation and the developer of the open-source HeuristicLab optimisation platform—and the Department of Mathematics at NIT Jalandhar, which carries expertise in mathematical optimisation, operational research, and applied quantum information. The collaboration will develop (i) surrogate-assisted multi-objective EA frameworks for VQE ansatz design, (ii) noise-aware evolutionary pulse optimisation with online hardware adaptation, and (iii) evolutionary hyperparameter search for quantum error-mitigation pipelines. Mutual visits, joint experiments on IBM Quantum hardware, co-supervised student exchange, and shared open-source software dissemination form the backbone of the exchange programme.

---

## Scientific Objectives

The project is organised around five scientific objectives, each directly addressable within the two-year timeframe:

1. **SO1 – Surrogate-Assisted Multi-Objective EA for VQE Ansatz Design.**
   Develop an NSGA-III framework with Gaussian-process (GP) graph-kernel surrogate to simultaneously minimise ground-state energy error, circuit depth, and hardware noise sensitivity for molecular VQE. Demonstrate a ≥ 10× surrogate speedup and first systematic Pareto front of ansatz structures for H₂, LiH, and BeH₂.

2. **SO2 – Noise-Aware Co-Evolutionary Pulse Optimisation with Online Surrogate Updating.**
   Design a CMA-ES / co-evolutionary system that evolves superconducting gate pulses alongside a neural-network noise surrogate continuously updated from real hardware. Show that fidelity robustness is maintained across 24-hour hardware drift windows.

3. **SO3 – Multi-Objective Evolutionary Discovery of Quantum Error-Correcting Codes.**
   Apply MOEA/D-driven genetic programming to search the stabiliser-code space, jointly maximising code distance, encoding rate, and transversal gate-set richness—a three-objective problem not yet addressed in the literature.

4. **SO4 – Neuroevolution for Barren-Plateau-Resistant QNN Architecture Search.**
   Adapt NEAT to quantum circuits (Q-NEAT) with an explicit gradient-variance objective to discover architectures that provably avoid barren plateaus, and build a theoretical understanding of the topology–plateau relationship.

5. **SO5 – Evolutionary Hyperparameter Optimisation of Quantum Error-Mitigation Pipelines.**
   Use NSGA-II with an ordered-sequence EA representation to identify Pareto-optimal compositions of error-mitigation techniques (ZNE, PEC, DD, M3) that balance residual error, circuit overhead, and hardware-call cost.

---

## Current State of the Research / Technology of the Topic

### Evolutionary Algorithms in Optimisation

Evolutionary Algorithms—encompassing Genetic Algorithms (GA), Genetic Programming (GP), Evolution Strategies (ES, CMA-ES), Differential Evolution (DE), and multi-objective variants (NSGA-II/III, MOEA/D)—are gradient-free, population-based metaheuristics that have been applied across engineering, bioinformatics, logistics, and machine learning. The HEAL Laboratory at FH OÖ Hagenberg is internationally recognised for its theoretical and applied contributions: the group developed HeuristicLab, an open-source, algorithm-independent optimisation framework with thousands of users worldwide, and has published extensively on surrogate-assisted EAs, symbolic regression via GP, and algorithm selection. Professor Affenzeller's research group brings deep expertise in: (i) surrogate-assisted evolutionary optimisation (GP surrogates, neural network surrogates, GP-with-GP surrogates); (ii) multi-objective Pareto optimisation for engineering design; (iii) symbolic regression and interpretable machine learning; and (iv) algorithm portfolio and selection methods. These algorithmic capabilities are directly applicable to the quantum computing domain.

### Quantum Computing on NISQ Devices

NISQ hardware (devices with 50–1000 qubits but without full fault tolerance) represents the near-term frontier of quantum technology. Key algorithmic paradigms include: the Variational Quantum Eigensolver (VQE) for quantum chemistry and materials simulation; the Quantum Approximate Optimisation Algorithm (QAOA) for combinatorial optimisation; Quantum Machine Learning (QML) via quantum neural networks (QNNs); and quantum simulation of many-body physics. All these paradigms rely on parameterised quantum circuits whose structure (ansatz) and parameters must be optimised—a task where classical gradient methods frequently fail due to barren plateaus, non-differentiable hardware models, and strongly discrete circuit structure.

The Department of Mathematics at NIT Jalandhar brings expertise in mathematical programming, metaheuristic optimisation, and applied quantum information theory. The Indian team's background in operational research and quantum algorithms provides the mathematical foundations for rigorous problem formulation and theoretical analysis that the proposed EA extensions will require.

### Gaps in the Current Literature

Despite EA's natural suitability for the challenges in quantum computing, the following critical gaps remain:

- **Surrogate assistance is virtually absent** from quantum circuit optimisation despite exponential simulation costs.
- **Multi-objective formulations** of VQE and QAOA optimisation are underexplored; nearly all work uses scalar cost functions, hiding the rich Pareto structure.
- **Noise-aware pulse optimisation** via EAs has not been integrated with adaptive hardware feedback loops.
- **Quantum error-correcting code discovery** has been restricted to single-objective GA searches; multi-objective formulations are missing.
- **QNN architecture search** via neuroevolution lacks an explicit barren-plateau objective, leaving a theoretically critical dimension unaddressed.
- **Error-mitigation pipeline composition** has never been automated with multi-objective EA.

These gaps define the research programme of the present proposal.

---

## Proposed Activities Including Methodology of the Proposed Research Work

### Year 1 (Months 1–12)

**Activity A1 (Months 1–4): Surrogate-Assisted NSGA-III for VQE Ansatz Design (SO1)**
- Develop a Directed Acyclic Graph (DAG) encoding for quantum circuits in HeuristicLab.
- Implement a GP surrogate with a Weisfeiler-Lehman graph kernel to predict circuit energy error and noise sensitivity from circuit topology.
- Integrate NSGA-III with GP-based pre-screening: only circuits passing a GP uncertainty threshold proceed to expensive Qiskit Aer simulation.
- Benchmark on H₂, LiH, BeH₂; compare against standard NSGA-III, hardware-efficient ansatz + COBYLA, and random search.
- *Exchange visit 1 (Month 3–4):* Austrian team visits NIT Jalandhar; joint experimental design and implementation workshop; two PhD students per side begin cross-institutional co-supervision.

**Activity A2 (Months 3–7): Co-Evolutionary Noise-Aware Pulse Optimisation (SO2)**
- Implement CMA-ES pulse optimiser operating on piecewise-constant pulse envelopes (50–200 time steps per channel).
- Train an initial neural-network noise surrogate on IBM Quantum calibration data; develop an online Bayesian update scheme that incorporates new process-tomography measurements.
- Deploy on IBM Quantum (real hardware) for CX and CZ gate synthesis on 2-qubit pairs.
- Validate robustness over simulated and real 24-hour hardware drift windows.

**Activity A3 (Months 5–9): MOEA/D Stabiliser Code Discovery (SO3)**
- Represent stabiliser codes as binary symplectic matrices; define GP-style mutation (add/remove Pauli product from generator set) and crossover (generator subset exchange).
- Implement random-forest surrogate to filter dominated candidates before BP-OSD distance computation.
- Search for [[n, k, d]] codes with n ∈ {7, 10, 15, 20}; compare Pareto fronts against known code families (surface codes, colour codes).
- *Exchange visit 2 (Month 6–7):* Indian team visits HEAL Lab, Hagenberg; hands-on HeuristicLab training and joint code review.

**Activity A4 (Months 8–12): Q-NEAT for Barren-Plateau-Resistant QNN Architecture Search (SO4)**
- Adapt NEAT to quantum gate graphs: typed nodes (single-qubit rotations, CNOT, SWAP), qubit-edge annotations, speciation by structural compatibility.
- Add gradient-variance objective: log Var[∂L/∂θ_k] computed over 100 random initialisations per candidate architecture, approximated by a graph-convolutional network surrogate.
- Evaluate on quantum phase recognition, random circuit classification, and molecular property prediction (PennyLane + Qiskit Aer).

### Year 2 (Months 13–24)

**Activity A5 (Months 13–17): Evolutionary Error-Mitigation Pipeline Optimisation (SO5)**
- Encode error-mitigation pipelines as ordered lists of (technique, hyperparameter) tuples (ZNE, PEC, M3, DD); implement NSGA-II with variable-length list representation.
- Develop a random-forest surrogate on pipeline feature vectors (one-hot techniques + hyperparameters) to pre-screen non-dominated candidates.
- Test on VQE circuits, random Clifford circuits, and quantum-volume circuits using IBM Quantum noise models and real-device validation.
- *Exchange visit 3 (Month 14–15):* Austrian team visits NIT Jalandhar; progress review, joint manuscript preparation sessions.

**Activity A6 (Months 15–20): Integration and Cross-Paradigm Experiments**
- Integrate A1–A5 modules within HeuristicLab under a unified quantum-optimisation plugin architecture.
- Conduct cross-paradigm experiments: co-evolutionary quantum-classical interface optimisation (joint ansatz + classical post-processing via nested EA loops, per Gap 8 in the research ideas document).
- Benchmark against reinforcement learning, Bayesian optimisation, and gradient-based baselines across all problem classes.

**Activity A7 (Months 18–24): Dissemination, Software Release, and Future Planning**
- Finalise all journal manuscripts (target: 3–4 peer-reviewed articles; see Expected Results section).
- Release open-source software package *QuantumEA* integrated with HeuristicLab and Qiskit.
- *Exchange visit 4 (Month 20–21):* Indian team visits HEAL Lab for final integration sprint, dissemination workshop, and joint grant writing for follow-on projects (FWF/SERB joint call).
- Organise joint workshop/minisymposium at a major international conference (GECCO or CEC).

### Mobility Schedule Summary

| Visit | Direction | Duration | Timing |
|---|---|---|---|
| Visit 1 | Austria → India (PI + 1 PhD) | 2 weeks | Month 3–4 |
| Visit 2 | India → Austria (PI + 1 PhD) | 2 weeks | Month 6–7 |
| Visit 3 | Austria → India (PI + 1 PhD) | 2 weeks | Month 14–15 |
| Visit 4 | India → Austria (PI + 1 PhD) | 2 weeks | Month 20–21 |

Short-duration visits (one week) for conference co-attendance and manuscript finalisation may supplement the above.

---

## Detailed Description of the Indo-Austrian Co-operation (Justification / Rationale for Collaboration)

The collaboration is justified by a uniquely complementary skill set distributed between the two groups that neither can fully exploit alone.

**The Austrian team at HEAL Lab** is one of Europe's foremost centres for evolutionary computation. Prof. Affenzeller's group commands deep expertise in: surrogate-assisted evolutionary optimisation with multiple surrogate types (GP, neural networks, symbolic regression models); multi-objective Pareto optimisation; the HeuristicLab software infrastructure which has been used in dozens of international research and industrial projects; and algorithm analysis and benchmarking. However, the HEAL group does not have established quantum hardware access or the quantum information theory background necessary to formulate quantum circuit optimisation problems rigorously, to interface with quantum simulators at the circuit and pulse level, or to design physically valid quantum error-correcting codes.

**The Indian team at NIT Jalandhar** contributes mathematical programming foundations—including linear programming, integer programming, multi-objective optimisation theory—combined with quantum information theory knowledge that provides rigorous problem formulations and theoretically grounded evaluation criteria. NIT Jalandhar also provides an important bridging role in the Indian NISQ ecosystem through its relationships with IIT institutions and access to IBM Quantum through the IBM–IIT network, providing real-hardware validation capability.

**The collaboration fills the gap from both sides:**
- Austrian EA methodology gains a quantum-informed problem formulation partner and hardware access channel.
- Indian mathematical optimisation and quantum information expertise gains industrial-strength evolutionary computation software (HeuristicLab) and surrogate-model know-how that would take years to develop independently.

This is not a directional technology transfer but a genuine bilateral scientific exchange: five of the ten research ideas in the foundational document (see `research_ideas_EA_quantum.md`) require both partners' core competencies simultaneously. No third single institution combines HEAL's depth in evolutionary algorithm engineering with NIT Jalandhar's quantum information and applied mathematics expertise.

Furthermore, the Indo-Austrian S&T mobility programme's specific mandate—to build lasting research partnerships between Austrian and Indian research groups through personnel exchange—is ideally served by a project whose scientific outputs (open-source software, published Pareto frontiers, novel code families) are inherently collaborative and internationally visible, and whose exchange visits are structured to build human capital (co-supervised PhD students) rather than simply transferring data.

---

## Compatibility of Intentions of Both Sides with Regard to Individual Components of the Project, Working Method etc.

Both groups share a common scientific language—optimisation—and compatible working philosophies built around open-source software, reproducible experiments, and rigorous benchmarking.

**Shared scientific values:**
- Both groups practice open-source research. HEAL's HeuristicLab is BSD-licensed; NIT Jalandhar's quantum code will be released under the same terms.
- Both groups value benchmark-driven science: the EA community's tradition of rigorous comparison against baselines aligns with the quantum computing community's insistence on circuit-level reproducibility.
- Both groups work within the Python / IBM Qiskit / PennyLane ecosystem for quantum experiments, ensuring no toolchain incompatibility.

**Division of responsibility:**
- EA algorithm design, HeuristicLab implementation, and surrogate model engineering: HEAL (Austria).
- Quantum circuit problem formulation, quantum simulation configuration, noise-model calibration, and error-correcting code theory: NIT Jalandhar (India).
- Joint authorship of all publications and joint maintenance of the QuantumEA software package.

**Student exchange and co-supervision:**
- Two PhD students per side will be enrolled in cross-institutional co-supervision agreements, with each student spending at least one of the four exchange visits at the partner institution.
- This builds a generation of researchers fluent in both evolutionary computation and quantum information.

**Communication:**
- Bi-weekly video meetings (first Tuesday of each month: full team meeting; third Tuesday: PhD student progress meeting).
- Shared GitHub repository (`anupuam/India-Austria`) and project wiki for code, data, and manuscript drafts.
- Shared Notion workspace for milestone tracking and task assignment.

**HeuristicLab integration commitment:**
- HEAL commits to providing HeuristicLab plugin development support for quantum circuit representations and quantum simulator interfaces; NIT Jalandhar commits to providing domain expertise for test-case design and physical validation of all quantum results.

---

## Expected Results and Dissemination Plan

### Scientific Outputs

**Publications (target: 4 peer-reviewed journal articles and 4 conference papers):**

| # | Title (working) | Venue (target) | Timeline |
|---|---|---|---|
| J1 | "Surrogate-Assisted NSGA-III for Pareto-Optimal VQE Ansatz Design" | *IEEE Transactions on Evolutionary Computation* | Month 10–12 |
| J2 | "Co-Evolutionary Noise-Aware Pulse Optimisation with Online Surrogate Updating" | *npj Quantum Information* | Month 12–15 |
| J3 | "Multi-Objective Genetic Programming for Quantum Error-Correcting Code Discovery" | *Quantum Science and Technology* | Month 16–20 |
| J4 | "Barren-Plateau-Resistant QNN Architecture Search via Q-NEAT" | *Nature Machine Intelligence* (or equivalent) | Month 20–24 |
| C1–C4 | Progress reports, component results | GECCO, CEC, QIP, IEEE Quantum Week | Months 6, 12, 18, 22 |

**Software Release:**
- *QuantumEA v1.0*: Open-source HeuristicLab plugin suite providing quantum circuit DAG encodings, quantum surrogate models (GP graph kernel, GCN), NSGA-III/MOEA/D operators for quantum problems, and Qiskit/PennyLane fitness evaluation interfaces. Released at Month 18 under MIT licence on GitHub.

**Datasets:**
- *VQE Ansatz Pareto Library*: Pareto-optimal ansatz structures for H₂, LiH, BeH₂; ≥ 2,000 evaluated circuits with energy, depth, and noise-sensitivity metadata. Deposited on Zenodo.
- *Stabiliser Code Pareto Library*: Novel multi-objective Pareto front of [[n, k, d]] codes for n ≤ 20. Deposited on Zenodo.

### Follow-on Interactions

The project is explicitly designed as a seed for a larger funded programme. The follow-on plan includes:
- **Year 3–5 (post-project):** Joint application to the FWF (Austrian Science Fund) – SERB (India) bilateral call, scaling the collaboration to full project funding (€ 500k–1M level), including extended student exchange and hardware access agreements with IBM Quantum Network partners.
- **Long-term partnership:** Joint Master's-level course module on "Evolutionary Optimisation for Quantum Technologies" to be offered in hybrid format at both FH OÖ and NIT Jalandhar from Year 3.
- **Industry linkage:** Austrian quantum-software companies (e.g., ParityQC, Quantum Brilliance Europe) and Indian quantum startups (QNu Labs, BosonQ Psi) will be engaged in Year 2 through a technology-transfer workshop to assess industrial applicability of QuantumEA.

### Dissemination Channels

- **Academic:** Peer-reviewed journals (listed above), conference presentations, open-access preprints on arXiv.
- **Software community:** GitHub releases, PyPI package, documentation site, JOSS (Journal of Open Source Software) submission for QuantumEA.
- **Policy and industry:** One-page technical briefs for the Austrian Research Promotion Agency (FFG) and India's National Quantum Mission (NQM); presentation at Indo-Austrian Business Forum.
- **Public:** Institutional press releases; blog posts in plain language on HEAL Lab and NIT Jalandhar departmental websites.

---

## Outline Major Milestones on a Time-Scale of Months

| Milestone | Description | Month |
|---|---|---|
| M1 | Project kickoff: agreements signed, GitHub repository set up, HeuristicLab quantum plugin scaffold committed | 1 |
| M2 | DAG circuit encoding and NSGA-III baseline implemented in HeuristicLab; VQE benchmark suite (H₂, LiH) operational in Qiskit Aer | 3 |
| M3 | **Visit 1 complete** (Austria → India); joint experimental protocol for A1 and A2 finalised | 4 |
| M4 | GP graph-kernel surrogate integrated; NSGA-III + surrogate achieves ≥ 10× speedup on H₂ VQE benchmark vs. NSGA-III without surrogate | 6 |
| M5 | **Visit 2 complete** (India → Austria); pulse optimiser (CMA-ES) deployed on IBM Quantum hardware for CX gate synthesis | 7 |
| M6 | First Pareto front of VQE ansätze published (arXiv preprint); stabiliser code GP operators implemented; MOEA/D search commenced | 9 |
| M7 | Neural-network noise surrogate achieves < 2% error vs. process tomography; online update loop validated over simulated 24-hour drift | 11 |
| M8 | **Journal submission J1** (VQE Pareto front); Q-NEAT scaffold implemented; first GECCO conference paper submitted | 12 |
| M9 | MOEA/D stabiliser code search completes for n ≤ 15; at least one code family superior to known constructions identified on 2 of 3 objectives | 15 |
| M10 | **Visit 3 complete** (Austria → India); manuscript drafts J2 and J3 under joint review; QuantumEA v0.9 (beta) released on GitHub | 15 |
| M11 | Q-NEAT: first demonstration of gradient-variance-guided architecture search; theoretical topology–plateau relationship paper drafted | 18 |
| M12 | **QuantumEA v1.0 released** on GitHub with full documentation; all datasets deposited on Zenodo | 18 |
| M13 | Error-mitigation pipeline optimiser (SO5) benchmarked on 5 circuit classes; NSGA-II Pareto front of pipelines validated on real IBM hardware | 20 |
| M14 | **Visit 4 complete** (India → Austria); follow-on FWF–SERB proposal submitted; technology-transfer workshop held | 21 |
| M15 | **Journal submissions J3 and J4** completed; GECCO/CEC workshop proceedings paper submitted | 22 |
| M16 | All deliverables complete; final project report submitted to funding agencies; joint announcement of QuantumEA adoption by at least one external group | 24 |

### Activities Required per Milestone

- **M1–M2:** Software architecture design; benchmark circuit library setup; IBM Quantum account provisioning.
- **M3–M5:** Algorithm implementation; hardware access scheduling; first experimental data collection.
- **M6–M8:** Surrogate training and validation; Pareto front analysis; manuscript writing.
- **M9–M12:** Code discovery experiments; Q-NEAT implementation; software packaging and documentation.
- **M13–M16:** Pipeline optimisation experiments; final manuscript submissions; dissemination and follow-on grant writing.

---

## Ethical, Safety and Regulatory Issues

**Does the proposed work raise ethical, safety, or regulatory issues?**

The proposed research is purely computational and algorithmic in nature. It does not involve: human subjects or patient data; animal experiments; genetic modification; hazardous materials; classified or export-controlled technology; or dual-use research of concern (DURC) as defined by the EU or Indian national guidelines.

**Quantum Key Distribution (Ideas 12 in the foundational document) is not within scope of this proposal.** The project focuses on gate-level and pulse-level quantum circuit optimisation, variational algorithms, and error correction—none of which involve cryptographic material, privacy-sensitive data, or national-security-adjacent applications.

**Data management:**
- All benchmark data will be deposited in open-access repositories (Zenodo, GitHub); no personal data is processed.
- IBM Quantum hardware access is governed by IBM's standard academic-use terms; no special regulatory approvals are required.

**Computational resource use:**
- Classical HPC usage at FH OÖ and NIT Jalandhar follows institutional IT governance policies.
- No GPUs or specialised hardware beyond standard HPC clusters and IBM Quantum cloud access are required.

**Conclusion:** No special ethical approval, safety assessment, or regulatory authorisation is required for this project. The PIs confirm that all activities will be conducted in accordance with the codes of good scientific practice of the University of Applied Sciences Upper Austria and NIT Jalandhar.

---

## Expected Results of the Cooperation

### Joint Publications
Four target journal articles and four conference papers (detailed above) will carry joint authorship from both institutions, establishing a visible bilateral publication record.

### Open-Source Software
*QuantumEA* will be the primary tangible artefact: a reusable, well-documented plugin suite for HeuristicLab that lowers the barrier for other research groups worldwide to apply EA methodology to quantum circuit optimisation problems. A JOSS submission will ensure the software is formally citable.

### Datasets
The VQE Ansatz Pareto Library and Stabiliser Code Pareto Library (deposited on Zenodo with DOIs) will serve as community benchmarks and establish priority for the Pareto-structured view of quantum circuit optimisation.

### Novel Scientific Results with Potential Commercial Value
Three results have identifiable commercial potential:

1. **Noise-Aware Pulse Optimisation Framework (SO2):** Commercial quantum hardware vendors (IBM, IQM, Zurich Instruments, Rigetti) and quantum software companies face the problem of rapidly degrading gate fidelity due to hardware drift. The co-evolutionary online pulse optimiser directly addresses a commercially valuable calibration problem. A technology-transfer pathway via an Austrian industrial partner (e.g., AQT – Alpine Quantum Technologies, Innsbruck) will be explored in Year 2.

2. **Quantum Error-Mitigation Pipeline Optimiser (SO5):** Any company running variational quantum algorithms on NISQ hardware needs error mitigation. An automated, Pareto-optimal pipeline selector could be embedded in Qiskit Runtime or a commercial quantum cloud service. Discussions with IBM Quantum Network partners will be initiated.

3. **QuantumEA Software Platform:** The platform itself has commercial licensing potential as the quantum computing industry matures, particularly for industrial quantum simulation users in chemistry and materials science.

### Intellectual Property and Sharing

No IP rights are expected to arise from the purely algorithmic and open-source outputs of this project. Should a commercially exploitable invention be identified during the project:
- Both institutions will jointly notify their technology-transfer offices (TTOs) within 30 days of identification.
- IP ownership will be shared proportionally according to each institution's contribution, in accordance with the IP provisions of the Indo-Austrian S&T Cooperation Agreement.
- Any patent filing will list all contributing inventors regardless of institutional affiliation.
- Publication of scientific results will not be delayed beyond six months to protect IP; any patent application will be filed before public disclosure.

### Co-supervised PhD Theses
Two PhD students per side will complete theses with joint international co-supervision, directly building human capital in the intersection of evolutionary computation and quantum technologies—a skill set in global demand.

### Long-Term Bilateral Network
The project is designed to initiate a sustained, multi-decade research partnership: joint courses, a follow-on FWF–SERB funded project, and an industry liaison network spanning Austrian and Indian quantum ecosystems.

---

*Proposal prepared jointly by:*
*Prof. Dr. Michael Affenzeller, HEAL Laboratory, FH OÖ Hagenberg*
*Dr. Anupam Yadav, Department of Mathematics, NIT Jalandhar*
*Date: May 2026*
