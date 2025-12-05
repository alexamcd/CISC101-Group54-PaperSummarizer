Module 1: Intake & Setup
Purpose

Initialize the summarization task by validating and normalizing all inputs. Ensure sections, audience, and limits are properly structured before processing.

Responsibilities:

Parse provided section list and raw text blocks

Normalize section titles (case, spacing, ordering)

Identify missing, extra, or mislabeled sections

Detect empty or extremely short sections (< 50 words)

Determine whether long-paper chunking is required

Pre-register metadata for downstream modules

Inputs:

User-provided section list

Raw text for each section

Audience level (expert or layperson)

Per-section word limits

Outputs:

Cleaned & normalized section map

Metadata file indicating:

Missing sections

Short sections

Chunking required (True/False)

Preprocessed structures for Section Loop

Rules & Constraints:

Do not alter section content

Maintain the user-provided order

Never hallucinate section names

Flag but do not fix missing/short sections

Internal Steps:

Ingest user inputs

Normalize section titles

Verify alignment between provided titles and actual text

Count words per section

If any section exceeds context window, trigger chunking flag

Build metadata object for later modules

Failure / Warning Conditions:

Missing section → warning

Unknown section name → warning

Empty section → error flag

Section < 50 words → short-section warning
