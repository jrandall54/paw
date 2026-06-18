# The Pedagogical Agentic Workflow (PAW) Framework

> A guide to using AI coding assistants as structured tutors, not code generators.

---

## 1. Welcome to PAW

If you have ever used an AI coding assistant, you are likely familiar with the standard interaction. You ask for a feature. The AI generates a block of code. You paste it into your project. The application works. This process is highly efficient for production.

However, it is highly detrimental to long-term learning.

The Pedagogical Agentic Workflow (PAW) is a structured methodology that inverts this dynamic entirely. Instead of treating the AI as a junior developer who writes code on your behalf, PAW configures the AI to act as a rigorous, uncompromising tutor. Under PAW, the agent teaches concepts, verifies your understanding through quizzes, and **only presents code after you have proven that you comprehend the underlying principles.**

In this workflow, the final working application is a byproduct. **The learning is the goal.**

---

## 2. Is PAW Right for You?

PAW requires patience. It intentionally introduces friction into the development process to ensure comprehension.

**PAW is designed for:**

* Beginners learning to code through project-based work.
* Self-taught programmers seeking structured rigor outside of a traditional classroom environment.
* Developers who want to avoid building a codebase they do not fully understand.
* Mentors seeking a repeatable framework to help students use AI safely and effectively.

**PAW is not designed for:**

* Experienced developers optimizing purely for speed and productivity.
* Teams that need to ship production code on a tight deadline.
* Prototyping projects where deep understanding of the underlying mechanics is unnecessary.

---

## 3. The Problem We Are Solving

Cognitive science identifies a phenomenon called the **illusion of competence** (Roediger & Karpicke, 2006). When you read a clear explanation or watch an AI generate perfectly formatted code, your brain easily processes the information. Because the material feels easy to read, you falsely assume it will be easy to retrieve and apply later. Passive exposure creates familiarity, not mastery.

When you copy AI-generated code without active cognitive effort, you produce a project you cannot debug, extend, or explain independently. PAW breaks this illusion by requiring you to actively retrieve information, predict structures, and explain reasoning at every step of the development journey.

---

## 4. The Architecture of Learning: Phase, Commit, Step

To make learning manageable, PAW breaks your project down into three nested scope levels. These levels mirror professional software development practices while creating natural boundaries for cognitive load.

### The Professional Mirror

| PAW Scope Level | What it represents in PAW | Professional Equivalent |
| :--- | :--- | :--- |
| **Phase** | A major milestone or feature set. | A minor version release (e.g., v0.1.0 to v0.2.0). |
| **Commit** | A single, logical addition to the codebase. | An atomic git commit ready for a Pull Request. |
| **Step** | A specific file or concept within a larger commit. | A file-level diff during code review. |

### The Pedagogical Benefit

This nested structure sequences your learning from abstract concepts down to concrete syntax:

* **At the Phase level,** you learn the big picture. What architectural patterns are we using? Why did we choose this database?
* **At the Commit level,** you learn specific design decisions. Why are we separating the controller from the service layer here?
* **At the Step level,** you learn the mechanics. What does this specific annotation do? Why did we write this exact line of code?

---

## 5. The Six-Stage Loop

The core mechanism of PAW is the Six-Stage Loop. Every unit of work you complete—whether it is a broad Phase or a specific Step—runs through this exact cycle. You cannot move forward until the current stage is complete.

| Stage | Name | Description | Gate Requirement |
| :---: | :--- | :--- | :--- |
| **1** | **OVERVIEW** | The AI explains the concepts you are about to use. | None |
| **2** | **PRE-QUIZ** | The AI tests if you understood the explanation. | You must pass the quiz and confirm readiness. |
| **3** | **PREDICTION** | You predict how the code will be structured. | None |
| **4** | **IMPLEMENTATION** | The actual code is presented and written. | None |
| **5** | **POST-SUMMARY** | The AI summarizes what you just built. | You must confirm you have reviewed the summary. |
| **6** | **POST-QUIZ** | The AI tests your understanding of the finished work. | You must pass the quiz and confirm readiness. |

### How the Loops Nest Together

Because the scopes are nested, the loops are nested as well. A Phase does not complete its "Implementation" stage until every Commit inside it has run through its own independent loop.

Here is a structural view of how the loops operate in practice:

```text
[ PHASE LOOP ]
 ├─ 1. Phase Overview
 ├─ 2. Phase Pre-Quiz
 ├─ 3. Phase Prediction
 ├─ 4. Phase Implementation
 │   │
 │   ├── [ COMMIT LOOP ] (repeats for each commit)
 │   │    ├─ 1. Commit Overview
 │   │    ├─ 2. Commit Pre-Quiz
 │   │    ├─ 3. Commit Prediction
 │   │    ├─ 4. Commit Implementation
 │   │    │   │
 │   │    │   └── [ STEP LOOP ] (if the commit touches multiple files)
 │   │    │        └─ Runs Stages 1 through 6 for the specific file
 │   │    │
 │   │    ├─ 5. Commit Post-Summary
 │   │    └─ 6. Commit Post-Quiz
 │   │
 ├─ 5. Phase Post-Summary
 └─ 6. Phase Post-Quiz
```

---

## 6. Deep Dive: What Happens in Each Stage

The following details what you will experience as you move through the six stages of a loop.

### Stage 1: Overview

Before you write any code, the agent will provide a comprehensive lesson on what you are about to do. It will introduce new APIs, explain design patterns, and define necessary vocabulary.

Crucially, the agent is instructed to always explain the **WHY** (the reasoning and design intent) before the **HOW** (the syntax and mechanics).

### Stage 2: Pre-Quiz

To ensure comprehension of the Overview, the agent will administer a short quiz.

| Scope | Minimum Questions |
| :--- | :--- |
| Phase | 3 |
| Commit | 2 |
| Step | 1 |

Quizzes are not simple vocabulary tests. The agent will ask **conceptual questions** (to check definitions) and **applied questions** (to evaluate if you can use the concept in a hypothetical scenario). You must pass this quiz to move forward.

### Stage 3: Prediction

This is the critical step for knowledge retention. Before the agent shows you the solution, it will ask you to predict what the code will look like. The agent might ask: *"What fields do you think this class needs?"* or *"What parameters should this function accept?"*

This stage is not graded, but it forces you to construct a mental model. When you finally view the actual code, your brain will immediately identify the differences between your prediction and the correct approach, solidifying the lesson.

### Stage 4: Implementation

During this stage, you write the code. The agent will present the code suggestion in a fenced block. **You are expected to type it out manually.** Copy-pasting bypasses the development of muscle memory and syntax familiarization.

If a commit is large, the agent will break it down into smaller Steps and guide you through them individually.

### Stage 5: Post-Summary

After the code is written and committed, the agent will provide a retrospective summary. It will connect the code you just wrote back to the abstract concepts discussed in Stage 1, establishing the bridge between theory and practice.

### Stage 6: Post-Quiz

The final verification. The agent will quiz you on the mechanics of the code you just built. It might ask you to trace the execution path, or ask what would break if you deleted a specific line of code. Once you pass this evaluation, you have completed the loop.

---

## 7. The Living Study Guide

A core component of PAW is the Study Guide (`study_guide.md`). The study guide is not a static document created at the end of the project, but a **living document** continuously maintained by the agent.

The agent must update the study guide at specific points in the loop to ensure it contains all relevant information up to that point:
* **After Stage 2 (Pre-Quiz)**: The agent records the core concepts taught in the Overview and the questions/answers from the Pre-Quiz.
* **After Stage 6 (Post-Quiz)**: The agent records the code design decisions from the Implementation, the Post-Summary takeaways, and the questions/answers from the Post-Quiz.

This ensures the study guide remains an up-to-date, comprehensive reference of your entire learning journey.

---

## 8. How You Will Be Evaluated

PAW agents are explicitly instructed to avoid sycophancy. If you provide a weak or incorrect answer, the agent will not politely agree with you or let it slide. It evaluates you based on strict standards.

| Verdict | Agent Behavior |
| :--- | :--- |
| **Correct** | You demonstrate genuine understanding. The agent will validate the answer and allow you to proceed. |
| **Partially Correct** | The agent will state exactly what you got right, point out what you missed, and ask you to try again. |
| **Incorrect** | The agent will explicitly state that the answer is incorrect, briefly re-explain the concept, and ask the question in a different way. |
| **Vague** | If you provide an unspecific answer (e.g., "it makes the data go to the database"), the agent will reject it and ask you to use proper technical terminology. |

### The Hint System

Struggling is an expected part of the learning process. If you fail a question twice, the agent will not hand you the answer. It will provide a targeted hint to guide your thinking, ensuring you arrive at the conclusion yourself.

### Persistent Misconception Detection

If you struggle with a concept in Phase 1, and then answer a question incorrectly about that same concept in Phase 3, the agent will detect the pattern. It will flag that you have a persistent misconception, discard its previous explanation, and teach the concept using a new analogy or framing.

---

## 9. Navigating the Workflow (Your Tools)

You remain in control of the workflow at all times. Use the following mechanisms to navigate the loop:

| Command / Tool | What It Does | How To Use It |
| :--- | :--- | :--- |
| **Inline Questions** | Pauses the loop to answer your question, then seamlessly returns you to your previous position. *(Note: If you ask for the answer during an active quiz, the agent will decline and offer a hint instead.)* | Simply ask a question in the chat at any time (e.g., *"Wait, what does orthogonal mean here?"*) |
| **`/explain [concept]`** | Immediately pauses the loop, provides a clear definition of the concept, explains how it relates to your current code, and resumes the loop. | Type `/explain` followed by the concept you want defined. |
| **`/sidebar`** | Bookmarks your exact spot in the loop and enters a free-flowing conversation mode for extended tangents or broader discussions. | Type `/sidebar` to enter. When finished, type "let's get back to it" to resume the loop. |
| **`/skip`** | Accepts your skip without penalty and moves to the next prompt. Use this sparingly—your skips are recorded in your study guide. | Type `/skip` to bypass a prediction step or a specific quiz question. |

---

## 10. The Science Behind PAW

PAW is heavily grounded in educational psychology and cognitive science.

| Principle | The Science | How PAW Uses It |
| :--- | :--- | :--- |
| **Retrieval Practice**<br>*(Roediger & Karpicke, 2006)* | Actively retrieving information from memory strengthens learning far more than passive re-reading. | The Pre-Quiz and Post-Quiz are the primary engines of your learning, forcing active recall. |
| **Desirable Difficulties**<br>*(Bjork, 1994)* | Making learning slightly harder in the short term (the "generation effect") leads to better long-term retention. | The Prediction stage forces you to generate ideas before seeing the answer, cementing the concepts. |
| **Mastery Learning**<br>*(Bloom, 1968)* | Students learn best when achievement is fixed at a high standard, but the time allowed to reach it is flexible. | The loop's readiness gates ensure you never carry partial understanding forward into the next lesson. |
| **Zone of Proximal Development**<br>*(Vygotsky, 1978)* | Learning happens in the zone between what you can do alone and what you cannot do at all. | The hint escalation system provides just enough scaffolding to keep you struggling productively. |
| **Metacognition**<br>*(Flavell, 1979)* | Being aware of your own thought processes improves how effectively you learn. | Applied quiz questions force you to evaluate your own mental models. |

---

## 11. Adapting PAW to Your Project

PAW is entirely agnostic to your technology stack. You can use it to build a web application, a command-line tool, or a mobile game. When you set up your project, you will instruct the AI to adapt the framework to your needs.

**Feel free to customize:**

* The programming language, framework, and tooling.
* Your specific code formatting and naming conventions.
* Your preferred git branching model.
* The minimum number of quiz questions for your scope levels.

**Do NOT customize:**

* The six-stage structure.
* The strict readiness gates between stages.
* The anti-sycophancy evaluation rules.
* The requirement for both conceptual and applied quiz questions.

> **If you remove the struggle, you remove the learning.**

---

## 12. A Glimpse Into a PAW Session

The following transcript demonstrates a complete cycle through a Commit-level loop. It shows how the agent guides the developer, evaluates answers, and presents code.

**Agent [Stage 1: Overview]**  
We are now on Commit #4: "Create the UserService class". This introduces the Service layer. We separate business logic from the Controller so we can unit test our business rules without needing to spin up the entire web framework. We will use the `@Service` annotation and constructor-based dependency injection.

**Agent [Stage 2: Pre-Quiz]**  
Question 1 (Conceptual): What is the primary responsibility of a Service class, and why don't we just put that code in the Controller?

> **Developer Answer:**  
> The Service handles business logic. The Controller should only handle requests and responses.

**Agent [Evaluation]**  
*Partially correct.* You identified the responsibilities correctly. However, you didn't explain *why* they are separated. What specific problem arises if business logic lives in the Controller?

> **Developer Answer:**  
> If it's in the controller, you can't test the business rules easily without setting up the whole web framework.

**Agent [Evaluation]**  
*Correct.* The key benefit is testability. Are you ready to proceed to the Prediction step?

> **Developer Answer:**  
> Ready.

**Agent [Stage 3: Prediction]**  
Before I show the code, tell me: what fields will `UserService` need to hold, and what methods do you think it will have?

> **Developer Answer:**  
> It will need a UserRepository field. Methods: createUser and findByEmail.

**Agent [Evaluation]**  
Good structural thinking. You correctly identified the dependency and two core methods. You missed that we will also need a `findById` method, which I will explain shortly. Proceeding to implementation.

**Agent [Stage 4: Implementation]**  
Here is the code suggestion for `UserService.java`. 

```java
@Service
public class UserService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
    // ... remaining methods
}
```

Please type this out and commit it.

> **Developer Answer:**  
> Done.

**Agent [Stage 5: Post-Summary]**  
In this commit, we created `UserService.java`. 

The class uses constructor injection: Spring sees the single constructor, recognizes that `UserRepository` is a managed bean, and automatically provides it. This allows our unit tests to instantiate `UserService` directly by passing a mock repository—no Spring context needed. 

Have you reviewed this summary?

> **Developer Answer:**  
> Yes.

**Agent [Stage 6: Post-Quiz]**  
Question 1 (Applied): If we removed the duplicate email check from the `createUser` method, what would happen when a user tries to register with an email that already exists in the database?

> **Developer Answer:**  
> The database would throw a constraint violation exception because the email column has a unique constraint. But it would be an ugly database error instead of a clean business exception.

**Agent [Evaluation]**  
*Correct.* The Service-level check converts an infrastructure error into a meaningful business error. 

Are you ready to move on to Commit #5?

> **Developer Answer:**  
> Let's go.

---

## Next Steps

Ready to start? The companion document, **PAW Getting Started Guide**, will walk you through exactly how to set up your environment, initialize your repository, prompt the AI to generate your project-specific instructions, and begin your very first session. 

Happy learning.

---
*PAW Framework v1.0.0*  
*Created: 2026-06-17*
