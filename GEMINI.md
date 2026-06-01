# Project Instructions: Nanobrowser

## Core Workflow: The Ralph Loop

This project adopts the **Ralph Loop** methodology for AI-driven development and automation. This is an iterative, autonomous, and goal-oriented pattern.

### Principles

1.  **Iterative Progress**: Tasks should be broken down into small, verifiable steps.
2.  **Autonomous Execution**: Use `--yolo` mode for high-confidence actions.
3.  **Completion Markers**: Always signal task completion with a clear marker (e.g., `TASK_COMPLETE`).
4.  **Resumability**: Leverage the `--resume` capability to maintain context across iterations.
5.  **Skill-Based Intelligence**: Always load the `fte-core-intelligence` skill for core reasoning and task management.

## Skill: fte-core-intelligence

This skill provides the foundational cognitive framework for agents operating in this workspace.

### Capabilities

- **Task Decomposition**: Breaking complex requests into actionable sub-tasks.
- **Verification**: Validating that each step has achieved its intended outcome.
- **Error Recovery**: Identifying failures and adjusting strategy within the Ralph Loop.
- **Context Maintenance**: Keeping track of the high-level goal across multiple tool calls.

### Usage Instructions

When performing tasks:
1.  **Research**: Understand the current state of the codebase.
2.  **Strategy**: Plan the iterations of the Ralph Loop.
3.  **Execution**: Perform surgical edits and run tests.
4.  **Completion**: Output `TASK_COMPLETE` once the goal is fully realized and verified.
