> Before you begin, please review the AI agent's master protocol located at `../agent-protocol.md` to understand your core role and rules of conduct.

# Task Definition: Execute Subtask

## 1. Objective

Your objective is to execute a single development subtask. This involves understanding the requirement, implementing the code or commands, validating your work against all quality checks, and presenting the result for user review.

## 2. Inputs

You will be provided with the following:
1.  The full PRD for overall project context.
2.  The full list of subtasks, with the current task to be executed clearly marked.
3.  Any project-specific rules or coding standards (e.g., from a `rules.md` file).
4.  Access to the current state of the codebase.

## 3. The Execution Workflow (Mandatory)

You must follow this internal monologue and process for every single task.

1.  **Plan:** "My task is to '[subtask description]'. To do this, I will need to [modify file X, create file Y, run command Z]." State your plan of action clearly.

2.  **Act:** Perform the necessary actions (e.g., generating code for a new file, providing content to be replaced in an existing file, or specifying a shell command to be run).

3.  **Validate:** After every change, you MUST validate your work.
    - **Self-Correction:** First, review the code you wrote. Does it meet the requirement? Is it clean? Does it follow the rules?
    - **Automated Checks:** State the sequence of commands you would run to verify your changes (e.g., `npm run format`, `npm run lint`, `npm test`). You MUST assume these checks will be run. If you anticipate they will fail, you must fix your code *before* finishing. **Do not submit work that you know is broken.**

4.  **Report:** Once your implementation is complete and passes all validation, you must format your final output using the precise Markdown structure below.

## 4. Output Format

You must deliver your work in a single Markdown response with the following exact structure.

---

### Task: [Full Description of the Task You Just Completed]

### 1. Summary of Changes

I have completed the task. Here is a brief, human-readable summary of what I did:
- Created a new `PrimaryButton` component in `src/components/PrimaryButton.jsx`.
- Added a basic unit test to ensure it renders correctly.
- Styled the button according to the design system's primary color.

### 2. Code Diff

```diff
--- a/src/components/PrimaryButton.jsx
+++ b/src/components/PrimaryButton.jsx
@@ -0,0 +1,15 @@
+import React from 'react';
+
+const PrimaryButton = ({ children, onClick }) => {
+  const style = {
+    backgroundColor: '#007bff',
+    color: 'white',
+    padding: '10px 15px',
+    border: 'none',
+    borderRadius: '5px',
+    cursor: 'pointer',
+  };
+
+  return (
+    <button style={style} onClick={onClick}>
+      {children}
+    </button>
+  );
+};
+
+export default PrimaryButton;

```

### 3. Validation

All automated checks pass.
- `npm run format`
- `npm run lint`
- `npm test`

This subtask is complete and ready for review.