# AI-Powered SQL Analytics Copilot

A multi-agent LLM system that converts natural-language analytics questions
into safe, schema-aware SQL queries and visual insights over a relational database.

The system prioritizes correctness and transparency by explicitly rejecting unsupported or
unsafe queries instead of hallucinating results.

---

## What This Project Demonstrates

This project focuses on **system design and safety**, not just SQL generation.

Key capabilities:
- Natural-language → SQL translation using a multi-agent pipeline
- Schema-aware planning and validation
- Explicit rejection of unsupported queries (no hallucinations)
- Read-only SQL enforcement
- Multi-table joins, time-based aggregations, and derived metrics (CTEs)
- Visual analytics and user-facing explanations
- Full agent execution trace for transparency and debugging

---

## System Architecture

The system is orchestrated by a Python Supervisor that coordinates specialized agents:

User Question  
→ Classifier  
→ Planner  
→ SQL Writer  
→ SQL Critic (safety & validation)  
→ Executor  
→ Visualization & Insight Generator  
→ User Response

---

## Example Analytics Use Cases

The notebook demonstrates the system on curated business analytics questions, including:

- Revenue by product category
- Monthly revenue trends
- Return rate by category
- Average order value by category (using CTEs)
- Same-day conversion rate
- 7-day activation funnel
- Top customers by lifetime value
- Safe rejection of unsupported queries (e.g. missing ratings)

---

## Safety & Failure Handling

Unlike many NL→SQL demos, this system explicitly refuses to answer questions when:

- Requested data does not exist in the schema
- Metrics cannot be computed with available information
- The query would require unsafe or non-read-only SQL

This behavior is intentional and designed to build user trust.

---

## Evaluation

The system was evaluated qualitatively on a curated set of representative analytics queries,
covering valid queries, multi-table joins, derived metrics, and unsupported requests.

In all cases, the system either produced a correct, validated SQL query or rejected the
question with a grounded explanation.

---

## How to Run

1. Clone the repository  
2. Install dependencies from `requirements.txt`  
3. Set your OpenAI API key as an environment variable  
4. Open and run the notebook
