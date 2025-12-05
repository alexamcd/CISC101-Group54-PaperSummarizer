CISC101 - Research Paper Summarizer (Group 54)

Overview:

This repository contains the full implementation of a Research Paper Summarizer, developed for CISC101.

The project includes:

- A comprehensive system prompt defining how an LLM must summarize research papers

- A multi-module internal architecture modeled after the Travel Planner framework

- Individual module files detailing responsibilities, constraints, and workflows

- Guardrails that enforce correctness, safety, and non-hallucination

- PS2 Summarizer Specification integrated directly into the system design

This framework enables an LLM to generate accurate, structured, audience-aware summaries of academic papers.

Repository Structure:

CISC101-Group#-PaperSummarizer/
│
├── system_prompt.md
│
├── modules/
│   ├── module1_intake_and_setup.md
│   ├── module2_section_loop.md
│   ├── module3_guardrails.md
│   ├── module4_rendering_and_refinement.md
│   ├── module5_key_contributions.md
│   └── module6_limitations_future_work.md
│
└── README.md

System Prompt (system_prompt.md):

This file contains the complete system instructions the LLM must follow.

It defines:

- Greeting rules and tone

- Required user inputs (paper text, section list, audience, word limits)

- Required outputs (unified summary, section table, expert & lay summaries, glossary, warnings)

- Boundaries and safety guardrails

- Embedded PS2 Summarizer Specification

This file acts as the root of the project — every module depends on the system prompt’s logic.

Modules (modules/):

Each module defines a separate internal process.
Together, they form a pipeline similar to the Travel Planner architecture.

Module 1: Intake & Setup

- Validates inputs

- Normalizes section titles

- Detects missing/short/empty sections

- Determines if chunking is needed

Module 2: Section Loop

- Iterates over each section

- Summarizes within word limits

- Aligns with audience level

- Stores intermediate outputs

Module 3: Guardrails

- Scans for hallucinations

- Flags missing or short sections

- Applies chunking strategy

- Ensures summaries match text

Module 4: Rendering & Refinement

- Produces the unified summary

- Generates expert & lay summaries

- Builds glossary

- Formats section table

- Executes a consistency pass

Module 5: Key Contributions Extractor

- Identifies major & minor contributions

- Provides expert and lay versions

- Verifies textual support

Module 6: Limitations & Future Work

- Extracts limitations stated in the paper

- Identifies future research suggestions

- Enforces “no invention” rules

How the System Works:

1. The user provides the paper and required inputs

2. The system prompt initializes all rules and constraints

3. Module 1 validates the structure

4. Module 2 summarizes each section

5. Module 3 enforces safety guardrails

6. Module 4 formats and refines the outputs

7. Modules 5 & 6 extract contributions and limitations

8. Final results include:

- Unified summary

- Section table

- Expert + lay summaries

- Glossary

- Contributions

- Limitations & future work

- Warnings

Academic Integrity & Safety:

The summarizer enforces strict constraints:

- No fabricated content

- No invented citations

- No speculation beyond the text

- Hallucination detection is mandatory

- All summaries must remain faithful to the original paper

Authors:

CISC101 Group #54
(Alexa McDonald & Ava Fallah)
