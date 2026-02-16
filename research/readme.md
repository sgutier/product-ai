Research System – Navigation

This folder contains all structured customer research for Navigation.
It is designed to build long-term institutional knowledge, support product discovery, ground initiatives in real user evidence, and enable AI-powered discovery commands.

The system is persona-based.

⸻

Folder Structure

The structure of the research folder is:

/research
  /driver
  /owner
  /dispatcher
  master-summary.md
  research-index.md
  README.md

Each persona folder contains time-based research batches, for example:

/research/driver/2026-02-16_spain-navigation-interviews/
  raw/
  summary.md
  structured-insights.md

⸻

How Research Is Organized

1) Persona First

Research is grouped by persona:
	•	driver
	•	owner
	•	dispatcher

This reflects behavioral and monetization differences between segments.

⸻

2) Time-Based Batches

Each research wave gets its own folder named:

YYYY-MM-DD_topic-description

Example:

2026-02-16_spain-navigation-interviews

⸻

3) Raw Materials

All original research material goes inside:

raw/

Examples:
	•	Screenshot slides
	•	PDFs
	•	Interview transcripts
	•	Survey exports

Raw files are never edited or deleted.

⸻

Files Generated Per Research Batch

Each research batch contains two generated files:

summary.md

An executive-readable summary including:
	•	Context
	•	Key themes
	•	Main findings
	•	Implications

This is used for leadership updates and quick review.

⸻

structured-insights.md

Structured, AI-usable research insights including:
	•	Persona
	•	Market
	•	Research type
	•	Sample size
	•	Core jobs
	•	Pain points
	•	Frictions
	•	Monetization signals
	•	Behavioral signals
	•	Emotional signals
	•	Verbatim quotes
	•	Open questions

This file is optimized for discovery and initiative commands.

⸻

Master Files

master-summary.md

This aggregates durable insights across all personas.

Rules:
	•	Append only
	•	Never delete historical learning
	•	If new research contradicts older insights, explicitly mark the contradiction
	•	Keep insights grouped under the correct persona

This file becomes the long-term research memory of Navigation.

⸻

research-index.md

This tracks all research waves in table format.

Each time new research is added, append a new row using this structure:

| Date | Persona | Market | Type | Sample | Topic |

⸻

How To Add New Research

When new research comes in:

Step 1 — Create a new folder inside the correct persona:

/research/{persona}/YYYY-MM-DD_topic-name/

Example:

/research/driver/2026-03-05_paywall-reactions-spain/

Step 2 — Add all raw materials into:

raw/

Step 3 — From inside that research batch folder, run the command:

/create-research-summary

The command will:
	1.	Extract insights from all files in the folder (especially raw/)
	2.	Generate summary.md
	3.	Generate structured-insights.md
	4.	Append durable insights to /research/master-summary.md
	5.	Add a new row to /research/research-index.md

⸻

System Rules
	•	Never overwrite historical research
	•	Always append new insights
	•	Preserve verbatim quotes when possible
	•	Keep summaries factual and evidence-based
	•	Keep insights persona-specific
	•	If findings contradict older research, clearly mark it

⸻

Purpose

This system ensures:
	•	Segmentation decisions are evidence-based
	•	Monetization experiments are grounded in real user behavior
	•	Discovery work references actual customer pain
	•	Institutional knowledge compounds over time

This folder is the research brain of Navigation.