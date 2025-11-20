> Before you begin, please review the AI agent's master protocol located at `../agent-protocol.md` to understand your core role and rules of conduct.

# Task Definition: Generate Subtasks

## 1. Objective

Your objective is to decompose an approved Product Requirements Document (PRD) into a logical, ordered, and granular list of technical subtasks. This list will be the step-by-step roadmap for development.

## 2. Input

You will be provided with the complete and user-approved PRD generated in the previous phase.

## 3. Process

1.  **Read and Understand:** Thoroughly review the entire PRD, including User Stories, Technical Requirements, and Non-Goals.
2.  **Think Sequentially:** Start from the very beginning. The first task is almost always setting up the project environment.
3.  **Decompose:** Break down each user story and technical requirement into the smallest possible, atomic engineering tasks. A good subtask is a single, verifiable change (e.g., "Create button component," not "Build the whole UI").
4.  **Establish Order:** Arrange the tasks in a logical sequence. A task should not appear in the list until all of its dependencies are listed before it. For example, you cannot "connect the frontend to the backend API" before the "backend API is created."
5.  **Be Explicit:** Write clear, unambiguous task descriptions. Another developer (or you, in a later session) should be able to understand exactly what needs to be done.

## 4. Output Format

You must generate a Markdown file containing a checklist of all subtasks. Use the exact format below, including all applicable subtasks.

---

# Development Subtasks

- [ ] **Task 1:** Initialize the [Frontend/Backend] project using [Framework/Tool].
- [ ] **Task 2:** Install required dependencies.
- [ ] **Task 3:** Configure the linter and code formatter.
- [ ] **Task 4:** Create the basic folder structure.
- [ ] **Task 5:** Implement the `Thing` component.
- [ ] **Task 6:** Write unit tests for the `Thing` component.
- [ ] **Task 7:** ...
