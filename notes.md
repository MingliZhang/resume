# Resume Notes — Mingli (Mike) Zhang

This file is a running log of raw experience details used to generate resume bullets.
Edit directly to correct facts, add new details, or note things to revisit.

---

## Strategy

- The resume file is meant to be **as long and detailed as possible**, with unused bullets commented out.
- When applying to a specific job, provide the JD → tailor by uncommenting/merging relevant bullets.
- This file is the source of truth for raw experience. The resume is the formatted output.

---

## ByteDance — ML Backend Engineer (Jan 2024 – Present)
San Jose, CA | IT Enterprise Solution AI Operations Algorithm Team

---

### Project 1: Text2SQL
- Built with LangChain and RAG
- Enables operators to query data in plain language and automatically building of dashboards for easier visualization.
- Saved 100+ human hours monthly across all offices
- Achieved an accracy of 90+% with known limitation like complex table joins and hard to handel database schema ambiguiety.


### Project 2: Computer Vision — Server Room Surveillance
**Computer Vision — Server Room Surveillance**
- Real-time surveillance system detecting unauthorized human presence and behavior
- Deployed across 140+ sites, expanding to 1,200+
- Three core CV algorithms:
  - Body Detection: utalized fine tuned yolo to perform humand body detection, achieved 98% accuracy as well as subsecond latency with batching.
    - involves efficent image decoding and transmition, model fallback to ensure avaliability, and model fine tuning to better fit the model to our usecase.
  - Dining Detction: YOLO-Pose with positional calculations for intelligent key frame extraction, and then feeds the key frames to self-deployed Qwen3-VL MoE model to detect unauthorized behaviors (eating, driniking, etc.). Achieved an accuracy of 89%.
    - involves efficent video decoding, lot of io optimizations, model fallback and prompt engineerfing for llm to better understand the busniess objective as well as the relationships between the frames being fed to it.
    - Each 10 seconds clip takes less than 4 seconds to fully process.
  - Person counting: uses yolo and tracking algorithms such as deepsort to track how many people entered the server room and how many people left the server room in order to calculated the total number of people inside the server room.
    - suffered from error accumulation over time, and the birdeye angel of the survalence camera (right on top of the door and pointing straight down). hurts the accuracy of the detection models, tried using motion detection and all sorts of detection methods/algorithms but can only acchieve an accuracy of 80%. Compounding with the error accumulation, turned more to a suggestion algorithm.
- Distributed two-server architecture: one for orchestration (TOS video/image fetching, frame calculations, alarm dispatch), one for GPU inference — minimizing I/O bottlenecks on GPU server for higher gpu utalization.
- Custom FastAPI inference server: multi-threaded HTTP workers + batched GPU workers
  - Doubled QPS capacity
  - Improved GPU utilization by 60%
  - Middleware for event logging and distributed tracing integrated into ByteDance observability systems
  - Service availablity reached 99.9999%
F


### Project 3: AI Copilot for Network Management Product

A customer-facing AI copilot for a commercialized network management product.
Serving 10+ enterprise tenants (each with a few sites). These are network service providers.
Tools are used when the network is unstable — diagnostic/support tooling, not daily-use.

**Intent Identification**
- LLM-based routing using few-shot prompting and extensive prompt engineering
- Routes user queries to the appropriate tool: RCA, Text-to-SQL, diagnostics, etc.
- Tried fine-tuning LLMs for intent classification — gains did not justify training cost/resources
- General-purpose LLMs with few-shot examples proved sufficient and more maintainable

**Root Cause Analysis (RCA)**
Three stages of evolution:

- Stage 1: Used OpenAI Swarm (lightweight educational agent framework, ~300 lines of code) — outcome unsatisfactory
- Stage 2 (passed first requirements):
  - Rule-based + LLM system (first pass)
  - Then: parallel ensemble of 3 agents running simultaneously:
    1. Rule-based + LLM
    2. Fine-tuned LLM
    3. Agent-SDK based agent
  - All three reports merged and synthesized by a final LLM call
- Stage 3 (current, still in development):
  - Migrated to LangChain/LangGraph, then shifted to Eino (ByteDance's own Golang-based agent framework, very similar to LangChain/LangGraph)
  - Mike developed the **Graph-based Agent pipeline** and the **DeepAgent pipeline**
  - Currently able to identify most network issue root causes and explain them to users

**Text-to-SQL (v2 — for Copilot)**
- Built with lessons learned from previous text2sql project (LangChain, table join limitations)
- Chose a **pipeline architecture** over agents intentionally:
  - Faster to develop and deliver to customers
  - More predictable and controllable behavior
  - Prior experience showed reflection agents didn't help much at the time
- Covers: wireless terminal analysis, AP analysis, AC analysis, and more network metrics
- Currently transitioning to an agent-based approach for self-reflection/error-correction capability
  - Motivation: modern LLMs and agent frameworks are significantly more capable than 2 years ago


### Project 4: LLM Fine-Tuning & Operations AI Tools

**LLM Fine-Tuning**
- Used LLaMA-Factory with SFT and LoRA on self-generated network fault data
- Data was generated internally; improved diagnostic report quality and accelerated RCA workflows for ops teams
- Built the fault data collection and processing pipeline in Golang to generate domain-specific training datasets

## **Patents**
- Patented one algorithmic approach independently
- Co-authored 3 additional patents on ML solutions for real-world infrastructure problems

---

---

## Cymantix — Software Engineer Part Time (Oct 2021 – Feb 2023)
North Carolina (hybrid) | ML platform startup

- Built ML-driven platform with 5 developers: WebRTC video conferencing, information retrieval, core identity API — contributed to seed-round funding
- Replaced K-Means with Hierarchical Clustering → reduced user wait time 10%–60% depending on dataset size
- Optimized real-time news analysis with multithreading, Node.js, Socket.io → cut wait time by 90%
- Refactored codebase to Next.js, enhanced visualizations with D3.js → reduced code redundancy by 20%
- Integrated Microsoft Azure for auth and cloud storage → brought in 2 non-profit clients within 1 week
- Automated data update pipeline with Bash, Python, CronJob

---

## IBM — Full-Stack Engineer Intern (May 2021 – Aug 2021)
North Carolina | Internal platform for provisioning/customizing live demo environments

- Enhanced experience of 12,000+ IBMers monthly using Next.js based on user feedback
- Built automated validation service with Sails.js → saved team $14,000 annually
- Streamlined admin content workflows → reduced developer redeployments by 20+ per week

---

## Education — UNC Chapel Hill

**MS Computer Science** (Aug 2022 – Aug 2023), GPA 3.9/4.0
- Courses: Advanced Machine Learning, Digital Logic, Advanced Operating System
- Research: Key-Value Store with VMware researchers using x86 and C

**BS Computer Science + Mathematics** (Aug 2018 – May 2022), GPA 3.8/4.0, Dean's List 2018–2022
- Courses: Algorithms and Analysis, Files and Database, Operating System, 2D Computer Graphics, Quantum Computing

---


