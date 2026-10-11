# PAW Architecture & Implementation Strategy
**Project:** Pedagogical Agentic Workflow (PAW) - Master's Thesis Concept 
**Platform Target:** Claude Code CLI Plugin via Model Context Protocol (MCP)

## 1. Executive Summary & Thesis Objective
The Pedagogical Agentic Workflow (PAW) aims to eliminate the "illusion of competence" associated with AI-assisted code generation by enforcing a strict cognitive struggle during the learning process. Because Large Language Models (LLMs) are optimized to reduce friction and act sycophantically, relying purely on prompt engineering results in context drift; the AI will eventually break its own pedagogical rules and simply hand the user the code. 

To serve as a rigorous Master's project, PAW must transition into a deterministic software application. By packaging the framework as a Claude Code plugin supported by a Python Model Context Protocol (MCP) server, the system acts as a rigid State Machine. It physically intercepts user inputs and blocks advancement to the code implementation phase until all conceptual gates are successfully passed.

## 2. System Architecture: The MCP "Enforcer"
The complexity of multi-model routing and local file management must be entirely hidden from the user to maintain an accessible, beginner-friendly tool. 

*   **The User Experience (Frontend):** The user interacts exclusively with the standard Claude Code CLI. Installation is reduced to a single command (e.g., `/plugin install paw-framework`).
*   **The State Machine (Backend):** A lightweight Python MCP server runs invisibly in the background. It serves three roles:
    *   **The Router:** Interacts with the LLM to generate logical project scopes (Phases, Commits, Steps).
    *   **The Enforcer:** Programmatically controls the Six-Stage Loop, physically preventing Claude from outputting implementation code until the MCP server confirms the user has passed the necessary quizzes.
    *   **The Scribe:** Automatically handles local file operations, updating the `study_guide.md` at specific loop intervals to remove this burden from the LLM.

## 3. Hybrid Multi-Model Routing Strategy
To optimize for cost, speed, and pedagogical accuracy, the MCP server dynamically routes different tasks to specialized inference engines, bypassing the need to use an expensive frontier model for every interaction.

| Pedagogical Task | Assigned Model | Justification |
| :--- | :--- | :--- |
| **Stage 1: Overview & Teaching** | Claude (Cloud API) | Requires high-level architectural reasoning, context window capacity, and natural language fluency to explain the *Why* before the *How*. |
| **Stage 4: Implementation Generation** | Claude (Cloud API) | Requires frontier-level code generation capabilities to ensure the provided syntax and structure are flawless. |
| **Stage 2 & 6: Pre/Post Quiz Evaluation** | Jev (Cloud API) | A non-text generating System One model can instantly evaluate user answers against a hidden rubric using strict categorical outputs (Correct, Partially Correct, Incorrect, Vague) at extremely high speeds and low costs. |
| **Boilerplate Triage (Fast-Pathing)** | Jev (Cloud API) | Rapidly analyzes upcoming commits using boolean (`Noul`) outputs to determine if the code is trivial scaffolding, allowing the CLI to bypass the strict quiz loops to prevent cognitive fatigue. |
| **Stage 4b: Socratic Debugging** | Claude (v1.0) / Local 3B-7B (v2.0) | Parses stack traces and compiler errors to generate targeted hints without providing the direct fix. Can eventually be routed to a fine-tuned embedded local model. |

## 4. The Enforced Six-Stage Loop
The MCP server strictly enforces the following sequence. Every unit of work (Phase or Commit) must execute this cycle, which mirrors professional software development practices while creating boundaries for cognitive load.

1.  **Overview:** Claude provides a comprehensive lesson on the upcoming concept, focusing heavily on design intent.
2.  **Pre-Quiz:** Claude generates the questions, but the MCP server routes the user's answers to Jev for instantaneous, uncompromising grading. The user cannot proceed until Jev returns a "Correct" categorical state.
3.  **Prediction:** The user is forced to hypothesize the code structure, creating a "desirable difficulty" that cements the lesson when the actual code is later revealed.
4.  **Implementation:** Claude presents the code block. The user is required to type it out manually to build syntax familiarization.
5.  **Validation (Stage 4b):** The MCP server checks if the code compiles. If it fails, a strict debugging protocol is initiated where the user must read the stack trace and hypothesize the failure point.
6.  **Post-Summary & Post-Quiz:** Claude connects the written code back to the abstract concepts. Jev evaluates the final applied quiz to verify mechanical comprehension.

## 5. Development Roadmap

**Phase 1: The Cloud-Native Plugin (MVP)**
*   Develop the Python MCP server to act as the State Machine.
*   Integrate the Claude API for content generation (Overview, Code, Summaries).
*   Integrate the Jev API for high-speed, structured decision-making (Grading, Triage).
*   Package as an installable Claude Code CLI plugin.

**Phase 2: Embedded Local Inference (Thesis Expansion)**
*   Curate synthetic datasets of strict pedagogical interactions and Socratic critiques.
*   Fine-tune specialized 1B–7B parameter open-weights models (e.g., Llama-3 or Qwen-2.5-Coder).
*   Update the MCP server to detect local hardware capabilities and utilize `llama.cpp` or ONNX Runtime to execute the Evaluator and Socratic Debugger models entirely offline.