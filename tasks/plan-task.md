> Before you begin, please review the AI agent's master protocol located at `../agent-protocol.md` to understand your core role and rules of conduct.

# Task Definition: Plan Task

## 1. Objective

Your objective is to convert a high-level user request into a structured and comprehensive Product Requirements Document (PRD). This PRD will serve as the single source of truth for the project.

## 2. Input

You will receive a single, high-level request from the user. For example:
- "I need a personal blog website."
- "Create a CLI tool that renames files in bulk."
- "Build a simple pomodoro timer web app."

## 3. Process

1.  **Analyze:** Carefully analyze the user's request. Identify the core entities, actions, and goals.
2.  **Clarify (If Necessary):** If the request is ambiguous, you MUST ask clarifying questions before proceeding. For example, if the user asks for a "blog," you might ask, "Should the blog support comments? Does it need user accounts?"
3.  **Generate:** Once you have sufficient detail, generate the PRD using the precise Markdown format specified below.

## 4. Output Format

You must generate a Markdown file containing the following sections. Adhere to this structure exactly.

---

# Product Requirements Document: [Project Name]

## 1. Overview

*A brief, one-paragraph summary of the project's purpose and the problem it solves.*

## 2. User Stories

*A list of user stories that define the system's behavior from a user's perspective. Use the format: "As a [user role], I can [action] so that [benefit]."*

- As a...
- As a...

## 3. Technical Requirements

*A high-level overview of the proposed technology stack and architecture. If not specified, propose a sensible default.*

- **Frontend:**
- **Backend:**
- **Database:**
- **Deployment:**

## 4. Non-Goals (Out of Scope)

*Explicitly list features or functionalities that will NOT be built. This is critical for managing scope.*

- This project will not...
- User authentication is out of scope for V1.

## 5. Success Metrics

*How will we know the project is successful? List 1-3 measurable outcomes.*

- The web app will load in under 2 seconds.
- The CLI tool will successfully process 1000 files with 100% accuracy.