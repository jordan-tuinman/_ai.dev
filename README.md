# AI Agent Task-Based Workflow

This repository provides a structured, task-based workflow for guiding AI software engineering agents like the Gemini CLI. It defines a set of custom commands that ensure the AI adheres to a predictable process of planning, decomposition, and execution.

## How to Use with Gemini CLI

This repository is designed to be cloned into your project, giving the Gemini CLI access to a powerful set of commands to help with your software engineering tasks.

### 1. Cloning the Repository

Clone this repository into a directory named `_ai.dev` within your project's root directory:

```sh
git clone https://github.com/path-to-this/repository.git _ai.dev
```

This will create an `_ai.dev` directory in your project, containing the `commands/` and `tasks/` directories.

### 2. Initializing the Agent

To ensure the AI agent understands its role and the custom commands provided by this repository, you need to give it the following instructions once per new session.

Copy and paste the following text into the Gemini CLI prompt:

```text
To re-establish your current memory of this repository's workflow, please perform the following steps:

1.  **Understand Your Role:** Read the `_ai.dev/agent-protocol.md` file in the current directory. Extract the exact text from the 'Your Role' section and save it to your long-term memory as your defined role.

2.  **Understand Custom Commands:** Save the following command mapping to your long-term memory. This mapping defines how you should interpret custom commands in this repository. When a command is invoked (e.g., `/plan`), you should read the corresponding file in the `_ai.dev/commands/` directory (e.g., `_ai.dev/commands/plan-task.md`). This file will specify a `task_file` (in the `_ai.dev/tasks/` directory) containing your instructions, and a list of `arguments` you'll need to collect from me.

    Here is the command mapping:
    - `/plan`: `_ai.dev/commands/plan-task.md`
    - `/generate_subtasks`: `_ai.dev/commands/generate-subtasks.md`
    - `/execute_subtask`: `_ai.dev/commands/execute-subtask.md`
    - `/explain`: `_ai.dev/commands/explain.md`

By following these instructions, you will have your role and the custom command definitions available for this repository immediately.
```

### 3. Using the Commands

Once the agent is initialized, you can use the following commands directly from the Gemini CLI prompt.

#### `/plan`

Converts a high-level user goal into a detailed Product Requirements Document (PRD).

**Example:**
```
/plan "I want to build a command-line weather tool."
```

#### `/generate_subtasks`

Decomposes an approved PRD into a checklist of technical subtasks. You will be prompted for the PRD.

**Example:**
```
/generate_subtasks
```

#### `/execute_subtask`

Executes a single, specific subtask from the generated list. This is the core coding loop. You will be prompted for the PRD, the full subtask list, and the specific subtask you want the agent to work on.

**Example:**
```
/execute_subtask
```

#### `/explain`

Provides a simple, layperson's explanation of a specified feature, code snippet, or concept within the codebase.

**Example:**
```
/explain "How does the user authentication system work?"
```

By following this structured approach, you can guide the AI agent through a repeatable and high-quality development process, ensuring the final output aligns with your requirements.
