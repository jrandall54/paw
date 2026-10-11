# PAW Beginner's Guide

> From an idea to your first PAW session -- step by step, assuming absolutely no prior coding knowledge.

This guide is the practical companion to the PAW Framework document. While the Framework defines *what* PAW is and *why* it works, this guide holds your hand through setting it up from scratch.

If you have never written a line of code in your life or have little experience in practical, hands-on software development, you are in the right place.

---

## Before You Begin

You need:
- A computer (Windows, macOS, or Linux)
- An internet connection
- A project idea (even a vague one -- "I want to build a to-do app" is enough)

You do **not** need:
- Prior programming experience
- A specific language or framework chosen in advance
- Any software pre-installed

---

## Step 1: Understanding AI Models & Credits

Since PAW relies entirely on AI agents acting as your tutor, it is vital to understand the tools powering them. The "brain" behind your agent is called a **Large Language Model (LLM)**.

### What are Credits?
AI platforms use vast amounts of computing power to generate responses. To manage this, they charge money or enforce usage limits using a system often called "credits" or "tokens." Long, complex questions cost more credits than short, simple ones.

As a beginner, being smart about which AI models you use will help you avoid running out of credits or encountering high usage bills.

### The Major AI Providers & Model Families

There are three primary companies that build the models most commonly used in AI coding assistants. Each family of models has a slightly different focus:

| Creator Company | Model Family | Key Coding Strengths |
| :--- | :--- | :--- |
| **Anthropic** | **Claude** | Known for exceptional reasoning, highly detailed natural explanations, and good adherence to workflow rules (like your PAW instructions). |
| **Google** | **Gemini** | Features massive "context windows" (the ability to read, analyze, and remember huge codebases all at once) and high-speed processing. |
| **OpenAI** | **GPT** | Highly reliable, fast responses, and widely compatible with nearly all external developer tools and extensions. |

### The Two Types of Models

Within each model family, the creator companies offer different sizes and strengths. They generally fall into two categories:

#### 1. Heavyweight Models
These are the largest, most intelligent models available. They act as "senior architects."

* **Examples:** Claude Opus (Anthropic), Gemini Pro (Google), the flagship GPT model (OpenAI). *Model names change every few months, so check your tool's model picker for the current versions.*
* **Strengths:** Exceptional reasoning, deep understanding of complex code, and excellent at high-level planning.
* **Weaknesses:** Slower to generate responses and cost significantly more credits per message.
* **Best Used For:** Creating your initial project roadmap, designing complex software architecture, or debugging a deeply confusing error.

#### 2. Speed & Efficiency Models
These are smaller, highly optimized models. They act as "fast, responsive tutors."

* **Examples:** Claude Sonnet / Claude Haiku (Anthropic), Gemini Flash (Google), the "mini" GPT models (OpenAI).
* **Strengths:** Lightning-fast responses and very cheap to use (costs far fewer credits).
* **Weaknesses:** Can occasionally struggle with massive, project-wide architectural overhauls without guidance.
* **Best Used For:** Running the PAW Six-Stage Loop. Because you will be going back and forth with the AI constantly (answering quizzes, getting hints, generating code snippets), a faster model saves you time and prevents you from burning through your credit limits quickly.

### PAW Setup Model Quick Reference

To help you manage your credits efficiently, here is a breakdown of which model to use at each stage of setting up and running PAW:

| Task / Step | Suggested Model | Why? |
| :--- | :--- | :--- |
| **Initializing Project & Git** (Step 6) | Heavyweight | Requires high-level planning to choose the right tech stack. |
| **Writing Instructions File** (Step 7) | Heavyweight | Translates framework rules accurately for your specific project. |
| **Creating Study Guide** (Step 8) | Heavyweight | Sets up the learning infrastructure flawlessly. |
| **Generating Roadmap** (Step 9) | Heavyweight | Requires deep architectural foresight to break the app into commits. |
| **Running the 6-Stage Loop** (Step 10+) | Speed & Efficiency | High volume of back-and-forth chat. Speed is essential; intelligence requirements are lower. |

---

## Step 2: Choose Your Project Idea

Before touching any tools, decide what you want to build. It does not need to be original, complex, or fully planned. It needs to be something you are genuinely interested in.

Here are some good starting ideas for absolute beginners, categorized by what you build and what you will learn:

| Project Idea | Project Type | What You Build | What You Learn |
| :--- | :--- | :--- | :--- |
| **Personal Portfolio Website** | Frontend Web | A static page showcasing your hobbies, resume, and contact details. | HTML structure, CSS layouts/styling, and basic interactive JavaScript. |
| **Classic Arcade Game** | Game Development | A simple control-based game like Snake, Pong, or a 2D maze explorer. | Game loops, user input detection, basic graphics rendering, and collision logic. |
| **Automated Desktop Organizer** | Scripting & Automation | A Python script that automatically categorizes and moves files in a target folder (like Downloads). | File system management, paths, handling file extensions, and automation scripts. |
| **Terminal-based Flashcard Tool** | CLI (Command Line) | A text-based application that quizzes you on definitions, tracks scores, and displays answers. | Loop structures, variables, storing user input, and terminal printing. |
| **Real-time Weather Dashboard** | API & Web | A web page that connects to a public API to retrieve and display current forecasts for any city. | Making HTTP requests, working with JSON data, and dynamic web page updates. |
| **Expense or Habit Tracker** | Productivity & Data | A basic application where you can log daily habits or purchases, compute totals, and display history. | State management, local storage, basic mathematical operations, and working with dates. |

Write your idea down in one sentence. Your AI agent will help you turn it into reality later.

---

## Step 3: Install an IDE with AI Agent Support

An **IDE** (Integrated Development Environment) is simply the application where you write code. It's like Microsoft Word, but for programmers. You need one that supports an AI coding agent built right in.

### Recommended Options

| IDE | AI Agent Support | Cost | Best Suited For & Notes |
|---|---|---|---|
| **[Antigravity](https://antigravity.google/)** | Built-in Antigravity agent | Free / Pre-configured | **Agentic developer workspace.** An AI-first environment designed by Google DeepMind for proactive agentic pair programming, featuring multi-tool execution and structured implementation plans. |
| **[VS Code](https://code.visualstudio.com/)** | GitHub Copilot, Cline, Continue, Roo Code | Free IDE (AI plugins have free/paid tiers) | **General-purpose coding.** Excellent for web development, scripting, games, and CLI tools. Extremely customizable. |
| **[Cursor](https://www.cursor.com/)** | Built-in Composer agent | Free tier available (Paid plans for high usage) | **AI-first general development.** Highly recommended for beginners; the AI agent has deep access to files and handles multi-file edits very smoothly. |
| **[Windsurf](https://windsurf.com/)** | Built-in Cascade agent | Free tier available (Paid plans for high usage) | **AI-first general development.** Similar to Cursor, but excels at interactive terminal debugging and collaborative coding sessions with the agent. |
| **[JetBrains PyCharm / IntelliJ (Community)](https://www.jetbrains.com/)** | JetBrains AI, GitHub Copilot | Free IDEs (AI requires separate subscription) | **Python and Java/Kotlin.** Best for heavy backend systems, Python automation scripts (PyCharm), or Java-based desktop/game development (IntelliJ). |
| **[Android Studio](https://developer.android.com/studio)** | Built-in Gemini developer assistance | Free | **Android Mobile Apps.** Tailored specifically for building native Android applications. |
| **[Xcode](https://developer.apple.com/xcode/)** | Swift Assist & Apple Developer tools | Free | **iOS/macOS Mobile Apps.** Required if you want to build native apps for Apple platforms (requires macOS). |

### How to Install
1. Click the link of your chosen IDE in the table above.
2. Download and run the installer for your operating system.
3. Open the IDE and sign in if required.

---

## Step 4: Create a GitHub Account

**GitHub** is a website that hosts code online. It serves as a secure backup for your project, a portfolio of your work, and the industry standard for sharing code. You will need an account before you can safely save versions of your project.

1. Go to [github.com](https://github.com).
2. Click "Sign up."
3. Follow the prompts to create a free account.
4. Remember the email address and username you choose; you will need them in the next step.

---

## Step 5: Install Git & Understand Version Control

Before you write code, you need a way to save it properly. **Git** is "version control" software.

### What is Version Control?
Imagine playing a difficult video game. Before fighting a boss, you save your game. If you lose, you can reload your save and try again. Git does exactly this for your code.

- **Repository (Repo):** Your project folder. It holds all your files and the history of every save.
- **Commit:** A save point. When you finish a small chunk of work, you "commit" it. If your code breaks later, you can rewind time back to any previous commit. *(In PAW, you will typically make a commit at the end of Stage 4: Implementation).*
- **Push:** Uploading your local commits from your computer up to GitHub (the cloud) so they are backed up safely.
- **Branch:** Creating an alternate timeline to experiment without breaking the main game.

### How to Install Git

**macOS**: Open the "Terminal" app (search for it in Spotlight) and type:
```bash
git --version
```
If Git is not installed, your Mac will ask if you want to install the "Command Line Tools." Click "Install."

**Windows**: Download Git from [git-scm.com](https://git-scm.com/download/win). Run the installer and keep clicking "Next" to accept all the default settings.

**Linux**: Open your terminal and run `sudo apt install git` (for Ubuntu/Debian) or the equivalent package manager command for your distribution.

### Configure Your Identity
Git needs to stamp your name on every "save point" (commit) you make. Open your Terminal (or the terminal panel inside your IDE) and run these two commands, replacing the placeholders with your actual name and the email you used for GitHub:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

## Step 6: Create Your Project

This is where you set up the actual code project. Because different apps require different languages, **your agent will do the heavy lifting here.**

### 6a: Ask Your Agent for Help
Open the AI chat panel in your IDE. *(Tip: Look for a chat bubble icon in the left or right sidebar, or try pressing `Cmd+L` on Mac or `Ctrl+L` on Windows).*

Ensure the agent is set to use a **Heavyweight model** (like Claude Opus or Gemini Pro), and tell it:

> "I want to start a new project. My idea is [your one-sentence idea]. I am a complete beginner with no prior coding knowledge. Can you help me choose a language and framework, and walk me through creating the project folder?"

### 6b: Initialize the Repository
Once the folder is created, you need to turn it into a Git repository so you can start saving your progress. Ask your agent:

> "My project folder is created. Can you walk me through the commands to run `git init` and push this code to a new, private GitHub repository?"

Your agent can often handle the technical initialization for you, or it will guide you step-by-step through your IDE's built-in interface. Simply follow its instructions carefully.

---

## Step 7: Create Your Agent Instructions File

This is the most critical file in a PAW project. It explicitly tells the AI **how to behave**. Without it, the AI will just write all the code for you, defeating the purpose of learning.

Tell your agent:

> "I want to use the Pedagogical Agentic Workflow (PAW) for this project. I am going to give you the PAW framework rules. Please help me create an `AGENTS.md` file in the root of my project that adapts these rules to my specific project."

Next, provide the agent with the text from the core **PAW Framework document**. If you do not want to copy and paste the entire body of text, most IDE chat interfaces provide simpler options:

- **Drag and Drop:** You can drag the PAW Framework file directly from your file explorer and drop it into the agent chat window.
- **Add File Button:** Look for a `+` (plus) sign or a paperclip attachment icon near the chat input box, which allows you to search for and select the file to add it as context.

If these options are not available in your IDE, simply open the framework document, copy its entire contents, and paste it directly into the chat.

The agent will read the rules, generate a project-specific instructions file, and save it in your project folder.

> **Important: the file name matters.** AI tools only read instruction files with specific names. `AGENTS.md` is read by most tools (Cursor, Windsurf, Copilot, Codex, and others). **Claude Code** reads `CLAUDE.md` instead. If you use Claude Code, either name the file `CLAUDE.md` or create a `CLAUDE.md` containing the single line `@AGENTS.md`. If the file has the wrong name, the AI never sees your PAW rules and will simply write the code for you.

> **A known limitation:** Even with the instructions file, AI agents can slowly drift away from the PAW rules during long sessions, and agentic IDEs may try to edit your files directly. If you notice the agent writing code into your files or skipping quizzes, remind it: *"Please follow the PAW rules in AGENTS.md. Do not edit my files; show me the code and I will type it."*

---

## Step 8: Let the Agent Create Your Study Guide

The **Study Guide** is a living document that accumulates every lesson, quiz, and prediction you make. It becomes a personalized textbook written specifically for you, by you and the AI.

> **Tip:** You can view this file at any time by opening your IDE's file explorer (usually on the left side of the screen) and clicking on the `study_guide.md` file. Keep it open in a tab next to your code!

**Formatting Note:** You do not need to provide a strict formatting template for the Study Guide. It is best practice to let the agent organically format and append to the document chronologically as you progress through your lessons.

Tell your agent:

> "Please create a new file at `docs/learning/study_guide.md` for this project. Give it a title and a brief introductory paragraph stating that it will record all PAW loop interactions, quizzes, and `/explain` concepts."

---

## Step 9: Create Your Roadmap

The **roadmap** breaks your grand idea into manageable, bite-sized pieces.

Tell your agent (using a Heavyweight model):

> "Help me create a development roadmap for this project. Break it into Phases (major milestones). For each Phase, list the individual Commits (save points) we will need. Each Commit should be a single, small, atomic change. Please save this as `docs/roadmap.md`."

---

## Step 10: Start Your First Session

You are ready! Switch your agent to a faster Speed/Efficiency model (like Flash or Sonnet) to conserve credits during the back-and-forth loop.

Open the AI chat in your IDE and say:

> "I am starting Phase 0, Commit 1 of my roadmap. Please begin the Stage 1 Overview."

The agent will take over from here, teaching you the concepts, quizzing you, and guiding you to write your very first lines of code.

### What to Expect
- **It will feel slow at first.** The quizzes and predictions take time, but they build genuine understanding.
- **You will get answers wrong.** This is normal! The agent will explain what you missed. Do not be discouraged.
- **Ask questions.** If a word or concept confuses you, just ask the agent to explain it.

---

## Navigating the Session: Commands & Workflow Expectations

During a PAW session, you remain in control of the learning flow. The AI agent acts as your tutor, but you can direct it, pause the lesson, ask for clarifications, or skip ahead using standard commands.

### The Slash Commands

You can type these commands directly into the AI chat window at any time:

| Command | What It Does | How & When to Use It |
| :--- | :--- | :--- |
| **`/explain [concept]`** | Pauses the active lesson to define a term, explain its relevance to your code, and save the definition directly to your Study Guide. | Use this whenever a new term, function, or library name appears in the code and you want a deeper explanation. *Example: `/explain database constraint`* |
| **`/sidebar`** | Pauses the structured PAW loop and opens a free-form discussion. This is perfect for asking hypothetical questions or exploring a tangent. | Use this when you want to explore "what if" scenarios without messing up the active lesson. When you are ready to resume, simply type *"let's get back to it"*. |
| **`/skip`** | Safely skips the current quiz question or prediction step without penalty. | Use this if you are genuinely stuck or if the quiz asks about a concept you already know thoroughly. *Note: All skips are logged in your Study Guide to help you track what you bypassed.* |
| **Inline Questions** | Pauses the loop to answer your question, then seamlessly returns you to your previous position. | Simply ask a question in the chat at any time for quick clarifications. *Example: "Wait, what does public static void mean here?"* |

### Workflow Expectations & Best Practices

To get the most out of PAW, keep these three rules of thumb in mind:

1. **Write Code Manually (Do Not Copy-Paste):** The AI agent will show you correct code snippets in Stage 4 (Implementation). You should manually type this code into your editor. Typing forces your brain to pay attention to syntax, punctuation (like semicolons and braces), and code structure. Copy-pasting bypasses this critical motor learning.
2. **Embrace the Struggle:** The quizzes are designed to test your actual understanding. If you answer incorrectly, the agent will not give you the code; it will offer hints to help you figure it out. This active struggle is how real learning occurs.
3. **Keep Your Study Guide Open:** The agent will automatically document your answers, explanations, and concepts in `docs/learning/study_guide.md`. Keep this file visible or check it periodically. It serves as your personal textbook, reflecting your progress and notes.

### Saving Your Code (Git)

Regularly backing up your work ensures you never lose progress. The easiest way to commit (save) and push (upload) your code to GitHub is to rely on your AI tutor.

Simply tell your agent: *"I have finished this commit. Please update my study guide and help me save and push my work to GitHub."* The agent will either handle the technical Git commands for you or guide you step-by-step through your IDE's built-in version control interface.

### Ending a Session

Ending a session properly is a highly recommended best practice. Standardizing how you stop ensures you don't lose your mental context. When you are ready to stop coding for the day, follow these steps:

1. **Finish the Current Loop:** Try to complete your active PAW loop (through Stage 6: Post-Quiz) before stopping. Stopping in the middle of a lesson makes it hard to pick up where you left off.
2. **Save Your Progress:** Follow the "Saving Your Code" steps above to back up your code to GitHub.
3. **Resume Easily:** Next time you sit down, just open the chat and tell the agent: *"I'm back. Let's start the next item on the roadmap!"*

Welcome to the world of programming. Happy learning!

---

*PAW Beginner's Guide v1.0.0*
*Companion to: The Pedagogical Agentic Workflow (PAW) Framework*
*Created: 2026-06-17*
