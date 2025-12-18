# Multi-Step-Reasoning-Agent-with-Self-Checking
Multi-Step Reasoning Agent with Self-Checking
📌 Overview

This project implements a Multi-Step Reasoning Agent capable of solving structured word problems (math, logic, constraints) by:

Breaking the problem into steps

Solving it systematically

Verifying its own solution

Returning only the final answer with a short explanation

The agent hides raw chain-of-thought reasoning and exposes only clean, user-friendly output, following modern LLM best practices.

🎯 Objective

Build an intelligent agent that:

Solves problems in multiple steps

Checks its own work before responding

Returns answers in a structured JSON format

Retries or fails gracefully if verification fails

🧩 Problem Types Supported

The agent handles problems such as:

🧮 Math & Arithmetic

Time differences

Counting problems

Multi-step calculations

🧠 Logic & Constraints

Slot scheduling

Capacity checks

Boundary conditions

Example Questions

“If a train leaves at 14:30 and arrives at 18:05, how long is the journey?”

“Alice has 3 red apples and twice as many green apples. How many apples in total?”

“Which time slots can fit a 60-minute meeting?”

🏗 Agent Architecture

The agent is divided into three clear phases:

User Question
     ↓
 Planner
     ↓
 Executor
     ↓
 Verifier
     ↓
 Final JSON Answer

🧠 Agent Phases Explained
1️⃣ Planner

Reads the user question

Produces a step-by-step plan

Example plan:

Parse input → extract values → compute → validate → format answer

2️⃣ Executor

Follows the planner’s steps

Performs calculations (via LLM or Python)

Produces intermediate results

3️⃣ Verifier

Independently checks the solution

Uses one or more strategies:

Re-solve the problem

Validate constraints

Check for inconsistencies

If verification fails:

The agent retries (limited times), or

Returns a failure response

📤 Output Format (JSON)
{
  "answer": "Final short answer",
  "status": "success",
  "reasoning_visible_to_user": "Short explanation",
  "metadata": {
    "plan": "Brief internal plan",
    "checks": [
      {
        "check_name": "Consistency Check",
        "passed": true,
        "details": "Verified successfully"
      }
    ],
    "retries": 0
  }
}


🔒 Note:
Full chain-of-thought reasoning is never exposed to the user.

🧪 Testing & Evaluation

The project includes test cases covering:

✅ 5–10 easy questions (basic math, time differences)

⚠️ 3–5 tricky questions (edge cases, ambiguity)

For each test, the system logs:

Question

Final JSON output

Verification status

Retry count

🛠 Technologies Used

Python

LLM API (OpenAI / Gemini / Anthropic or mocked)

JSON-based structured outputs
