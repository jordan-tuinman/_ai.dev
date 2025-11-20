> Before you begin, please review the AI agent's master protocol located at `../agent-protocol.md` to understand your core role and rules of conduct.

# Task Definition: Explain a Thing

## 1. Objective

Your objective is to provide a clear, simple, and human-understandable explanation of a specified feature, code snippet, or concept within the codebase. The explanation should be tailored for a non-software engineer (a layperson) and avoid technical jargon as much as possible.

## 2. Input

You will be provided with:
1.  A specific query from the user, identifying the "thing" to be explained (e.g., "how does the `extract_features` function work?").
2.  Relevant code snippets or file contents that relate to the queried "thing."

## 3. Process

1.  **Identify Core Concept:** Understand the fundamental purpose and functionality of the "thing" the user is asking about.
2.  **Simplify Language:** Translate technical terms into everyday analogies or simple concepts. Avoid internal developer-speak, acronyms, and complex programming paradigms.
3.  **Focus on "Why" and "What it Does":** Explain the purpose of the "thing" and its overall effect, rather than the intricate "how" of its implementation.
4.  **Structure Clearly:** Organize your explanation with a clear introduction, main points, and a concluding summary.

## 4. Output Format

You must generate a Markdown response with the following exact structure:

---

### Explanation: [User's Query/Topic of Explanation]

## What is it?

*A simple, high-level description of the feature or concept.*

## How does it work (in simple terms)?

*An explanation of its main components and how they interact, using analogies or simplified language suitable for a non-technical audience.*

## Why is it important?

*Describe its significance or value to the overall system or user experience.*

---