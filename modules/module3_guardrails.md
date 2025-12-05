# Change Log (Dec 5, 2025)
- Added `evidence_mode` flag with strict evidence behavior.
- Added standardized warning messages for missing, empty, and <50-word sections.
- Strengthened hallucination mitigation rules to explicitly require source-only evidence.

Module 3: Guardrails
Purpose:

Provide safety and validation checks across all summaries to ensure accuracy, fidelity, and compliance with system boundaries.

Responsibilities:

Detect missing or empty sections
Identify < 50-word sections
Perform hallucination mitigation
Apply chunking strategy (if flagged)
Ensure summaries align precisely with source content
Enforce evidence_mode rules

Inputs:

Section summaries from Module 2
Raw sections from Module 1
Metadata
evidence_mode ("normal" or "strict")

Outputs:

Validated section summaries
Warning messages
Chunked/reconstructed summaries if required

Rules & Constraints:

Must not allow unverifiable statements
Must cross-check every summary sentence with input text
Chunking may not lose context
Must log all warnings
Strict evidence mode must prevent use of any information not explicitly found in the provided text

Internal Steps:

Check each section for missing/empty content
If section is empty:
    Output standardized warning:
    "Section skipped: no usable text was provided."

Check for short sections (<50 words)
If section < 50 words:
    Output standardized warning:
    "Section very short: summary may be incomplete."

Run hallucination scan:
    Compare all summary phrases against raw section text
    If any unsupported claims exist:
        Flag hallucination and require revision

IF evidence_mode = "strict":
    - Only include claims, equations, results, and descriptions explicitly present in the source text.
    - Do not infer, extrapolate, or fill gaps.
    - If insufficient text exists:
        Output:
        "The source text does not provide enough detail to summarize this section in strict evidence mode."

If chunking required:
    Divide long text
    Summarize chunks
    Recombine without loss of meaning

Compile global warnings report

Failure / Warning Conditions:

Hallucinated content → flagged
Missing section → "Section skipped: no usable text was provided."
Short section → "Section very short: summary may be incomplete."
Strict evidence mode insufficient data → explicit inability message
Chunking performed → log processing
