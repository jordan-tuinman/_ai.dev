# Task: Diagnose Web Page

You will be provided with a URL. Your goal is to navigate to the page, gather diagnostics, identify potential issues, and generate a concise report in a dynamically named markdown file.

## Tooling and Process

This task is completed by me, a large language model, following a structured, model-driven process. I will use the following tools to gather and save data:

*   **Browser Interaction:** `navigate_page`, `list_console_messages`, `list_network_requests`, `take_snapshot`
*   **File System:** `run_shell_command` (to create the directory), `write_file` (to save the report)

The analysis of the collected data is a cognitive process based on the instructions below.

## Instructions

### Step 1: Prepare Output Path
1.  Ensure a directory named `diagnose` exists. If not, create it.
2.  Parse the hostname from the `url` (e.g., `www.example.com`).
3.  Get the current timestamp in `YYYY-MM-DD_HH-MM-SS` format.
4.  Construct the output path: `diagnose/<hostname>_<timestamp>.md`.

### Step 2: Navigate and Collect Data
1.  Use `navigate_page` to go to the provided `url`.
2.  Use `list_console_messages` to get all console logs.
3.  Use `list_network_requests` to capture all network activity.
4.  Use `take_snapshot` to capture a text-based representation of the final rendered page content.

### Step 3: Analyze for Issues
1.  **Critical Errors:** Scrutinize the console messages for any with `type: 'error'`. Check network requests for any with a status of 400 or higher.
2.  **Rendering Gaps:** Compare the `take_snapshot` output to what you might expect. Are key components missing?
3.  **Warnings & Observations:** Note any console warnings (`type: 'warn'`) or other relevant observations.

### Step 4: Synthesize and Generate Report
1.  Based on your analysis, form a hypothesis about any issues.
2.  Use the `write_file` tool to save the report to the path constructed in Step 1, using the concise template below.

---
## Report Template
````markdown
# Web Page Diagnostics: {{url}}

**Generated:** `date`

## 1. Summary

*Brief, high-level summary of the page's health. Example: "The page loaded but failed to render the main content area due to a critical JavaScript error." or "The page appears healthy with no critical errors detected."*

## 2. Potential Issues Detected

*A bulleted list of observed issues, categorized for clarity. If a category has no issues, state "None detected."*

### 🔴 Critical Errors (High Confidence)
*   **(Category: e.g., Console/Network)**: Brief description of the error. **Impact**: What this error is likely causing.

### 🟡 Warnings (Medium Confidence)
*   **(Category: e.g., Console/Rendering)**: Brief description of the warning or issue. **Impact**: What this could be affecting.

### 🔵 Observations (Informational)
*   **(Category: e.g., Network/Rendering)**: An observation that may be of interest but is not an immediate error.

## 3. Supporting Data

### Key Console Messages
```
{{console_messages}}
```

### Failing Network Requests
```
{{network_requests}}
```

### Rendered Page Snapshot
```
{{snapshot_content}}
```
````
---