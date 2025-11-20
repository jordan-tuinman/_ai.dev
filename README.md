# AI Agent Task-Based Workflow

This repository provides a structured, task-based workflow for guiding AI software engineering agents like the Gemini CLI. It ensures that the AI adheres to a predictable process of planning, decomposition, and execution.

The workflow is defined by a master protocol (`agent-protocol.md`) and a set of task-specific definition files located in the `tasks/` directory.

## How to Use with Gemini CLI

### Initial Setup for Gemini CLI

To ensure the AI agent understands its role and the custom commands provided by this repository from the start of any new session, use the following prompt. This needs to be done once per new agent instance where this repository is present.

```text
"To re-establish your current memory of this repository's workflow, please perform the following steps:

1.  **Understand Your Role:** Read the `_ai.dev/agent-protocol.md` file in the current directory. Extract the exact text from the 'Your Role' section and save it to your long-term memory as your defined role.

2.  **Understand Custom Commands:** Save the following command mapping to your long-term memory. This mapping defines how you should interpret custom commands in this repository. When a command is invoked (e.g., `/plan`), you should read the corresponding file in the `_ai.dev/commands/` directory (e.g., `_ai.dev/commands/plan-task.md`). This file will specify a `task_file` (in the `_ai.dev/tasks/` directory) containing your instructions, and a list of `arguments` you'll need to collect from me.

    Here is the command mapping:
    - `/plan`: `_ai.dev/commands/plan-task.md`
    - `/generate_subtasks`: `_ai.dev/commands/generate-subtasks.md`
    - `/execute_subtask`: `_ai.dev/commands/execute-subtask.md`
    - `/explain`: `_ai.dev/commands/explain.md`

By following these instructions, you will have your role and the custom command definitions available for this repository immediately."
```

The core idea is to use the content of a task file as the system prompt or context for the Gemini CLI at each phase of the development cycle. You can do this by piping the file content directly into the `gemini` command.

---

### Phase 1: Plan the Project (`tasks/plan-task.md`)

This phase converts a high-level user goal into a detailed Product Requirements Document (PRD).

**1. Provide the Goal:** Start with your project idea.
**2. Run the Command:** Use the `plan-task.md` file to instruct the AI to create a PRD.

**Example:**
```sh
# The AI will prompt you for the user request after receiving the instructions.
cat tasks/plan-task.md | gemini -p - "My user request is to build a command-line weather tool."
```

---

### Phase 2: Generate Subtasks (`tasks/generate-subtasks.md`)

Once you have an approved PRD, use this phase to get the AI to decompose it into a checklist of technical subtasks.

**1. Provide the PRD:** Copy the PRD generated in Phase 1.
**2. Run the Command:** Use `generate-subtasks.md` and paste the PRD when the AI prompts you.

**Example:**
```sh
# The AI will prompt you for the PRD after receiving the instructions.
cat tasks/generate-subtasks.md | gemini -p - "Here is the PRD: ..."
```

---

### Phase 3: Execute a Subtask (`tasks/execute-subtask.md`)

Execute a single, specific subtask from the generated list. This is the core coding loop.

**1. Provide Context:** Give the AI the `execute-subtask.md` instructions, the PRD, the full subtask list, and the specific subtask you want it to work on.
**2. Run the Command:** The AI will generate the code and a report.

**Example:**
```sh
# Provide all context in a single prompt.
PROMPT="
Here is the PRD: [Paste PRD Content Here]

Here is the full subtask list: [Paste Subtask List Here]

You are to execute this subtask: '[The specific subtask description]' 
"
cat tasks/execute-subtask.md | gemini -p - "$PROMPT"
```

---

### Phase 4: Explain a Thing (`tasks/explain-thing.md`)

This task provides a simple, layperson's explanation of a specified feature, code snippet, or concept within the codebase.

**1. Provide Context:** Give the AI the `explain-thing.md` instructions and your query. You might also include relevant code files.
**2. Run the Command:** The AI will provide a simplified explanation.

**Example:**
```sh
# Provide the explanation instructions and your query.
# Optionally, include code content for context.
PROMPT="
My query is: 'How does the user authentication system work?'
Here is the relevant code from `src/auth.js`:
```javascript
// ... content of src/auth.js ...
```
"
cat tasks/explain-thing.md | gemini -p - "$PROMPT"
```

---

By following this structured approach, you can guide the AI agent through a repeatable and high-quality development process, ensuring the final output aligns with your requirements.