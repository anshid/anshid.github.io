---
layout: page
title: Goal Finisher Custom GPT
permalink: /projects/ai-goal-finisher/
---

## 1. Problem Statement
General Large Language Models (LLMs) act as submissive conversational partners, often failing to act as accountability partners. The Goal Finisher GPT flips the instruction paradigm by assigning the AI a structured authoritative role, utilizing prompt engineering schemas to strictly enforce task breakdown and completion tracking rather than generalized conversation.

## 2. Prompt Engineering Constraints
The model relies heavily on behavioral guardrails set during the configuration phase:
- **Tone Modification**: Instructed to remain firm, objective, and task-oriented.
- **Structural Enforcement**: Enforces a rigid step-by-step breakdown (breaking a large goal into atomic sub-tasks). 
- **Accountability Checks**: Refuses to proceed or generate long ideation unless the user confirms completion of the immediate preceding sub-task.

## 3. Product Features
- Dynamic step enumeration (adapting to user feedback).
- Progress validation checks.
- Zero-fluff execution (avoiding the conversational filler native to standard ChatGPT).

## 4. Observations & Iteration
While dogfooding the product, prompt decay was observed where the system would sometimes revert to "helpful assistant" mode, providing the answers rather than waiting for user action. Incremental updates to the system instruction block were required to prioritize strict workflow adherence.

**Live Link**: [Goal Finisher (Custom GPT)](https://chatgpt.com/g/g-6975af95f7808191a7c1ecf2d249018e-goal-finisher)

## 5. Future Scope
- Expand the instruction set to allow users to ask "what is the strategy?" without breaking the accountability loop.
- Package the underlying prompt logic into an independent API to be integrated into productivity frontend ecosystems via custom tooling.
