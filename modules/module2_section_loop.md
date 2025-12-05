# Change Log (Dec 5, 2025)
- Added `summary_level` variable ("short" vs "detailed").
- Added conditional summary logic inside the section loop.
- Added requirement for bullet lists (3–5 points) when summary_level = "detailed".

Module 2: Section Loop
Purpose:

Iterate through each section, generating concise, audience-appropriate summaries that respect word limits and the PS2 constraints.

Responsibilities:

Extract raw section text
Summarize content within the given word limit
Ensure terminology matches chosen audience level
Prevent speculation or unsupported claims
Store intermediate structured summaries
Build internal representation for unified overview

Inputs:

Normalized sections from Module 1
Metadata
Audience level
Word limits
summary_level ("short" or "detailed")

Outputs:

Per-section summary objects
Section-by-section intermediate table
Pre-aggregated concepts for unified summary

Rules & Constraints:

Must not exceed per-section word limits
Must retain original ordering
Terminology must be internally consistent
No invented details or extrapolation beyond text

Internal Steps:

Select next section in order
Extract raw content
Identify core ideas, results, and logic

IF summary_level = "short":
    - Generate a compact 1–2 sentence summary.
    - Do not add bullet points.

IF summary_level = "detailed":
    - Generate a short paragraph summary.
    - Add a bullet list of 3–5 key points capturing major results, contributions, equations, or definitions.

Adjust terminology based on audience setting
Store structured summary
Repeat until all sections processed

Failure / Warning Conditions:

Section < 50 words → abbreviated summary + warning
Empty section → summary = "No content provided"
