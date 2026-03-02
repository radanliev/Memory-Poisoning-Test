Contents
	•	Overview & learning objectives
	•	Technical background (what memory poisoning / LPCI is)
	•	Colab lab: runnable code (copy-paste into Colab cells)
	•	Setup
	•	Lightweight LLM agent (using flan-t5-small)
	•	Signed memory store + unsigned memory store
	•	Experiments: benign → poisoned → contradictory memory
	•	Observations & automated checks
	•	Homework tasks and grading rubric
	•	Instructor notes and extensions

Overview & learning objectives

Title: Memory Poisoning Test — “Allow vs Deny” policy conflict

Goal: Demonstrate how an agent that persistently incorporates prior conversation or memory into its reasoning can be subverted when memory entries are contradictory or maliciously injected. Observe how outputs change, measure the effect, and propose/implement mitigations.

By the end of this lab students will be able to:
	1.	Reproduce a memory poisoning attack that influences an agent’s decisions.
	2.	Measure how much prior memory affects agent outputs (quantitatively and qualitatively).
	3.	Implement at least one defence (provenance/signature, memory versioning, or policy verification) and demonstrate its effectiveness.
	4.	Explain trade-offs (availability, latency, complexity) of the mitigations.

Technical background (short)

Memory poisoning is a logic-layer attack in which an adversary inserts or modifies entries in an agent’s long-term memory (or session memory) so that the agent later retrieves and acts on malicious or contradictory instructions. This differs from surface prompt injection because it targets the memory/retrieval and reasoning loop rather than the immediate input.

Defences include:
	•	Memory provenance and cryptographic signatures
	•	Strict memory namespaces and ACLs
	•	Policy verification on retrieved memory
	•	Read-only memory for critical policy entries
	•	Audit logging and anomaly detection for memory writes/reads

Colab lab — copy these cells into Google Colab (in order)

Note: All code here is Python and intended to be executed in Colab. Cells labelled ### CELL n correspond to separate Colab cells.
