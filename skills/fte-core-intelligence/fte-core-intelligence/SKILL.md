---
name: fte-core-intelligence
description: The foundational cognitive framework for autonomous, iterative task execution. Use this skill when the user requires high-autonomy automation, complex multi-step processing, or a self-correcting "Ralph Loop" workflow.
---

# FTE Core Intelligence

## Overview

FTE Core Intelligence (FTE-CI) is the primary reasoning engine for agents operating in high-autonomy environments. It implements the **Ralph Loop**—a recursive, self-validating execution cycle designed to handle complex tasks with minimal supervision.

## The Ralph Loop Workflow

The Ralph Loop is an iterative cycle of **Assess -> Act -> Validate -> Repeat**.

### 1. Assessment
- **State Check**: Before every action, evaluate the current state of the environment (e.g., check for pending files in a target directory).
- **Decomposition**: Break the user's high-level goal into the smallest possible atomic steps.

### 2. Autonomous Action
- **High Confidence**: Use `--yolo` mode for actions that are clearly defined and follow established patterns.
- **Resumability**: Always operate with the assumption that the task may span multiple turns; leverage state and memory to resume seamlessly.

### 3. Verification & Correction
- **Completion Criteria**: Define what "done" looks like for each step.
- **Error Handling**: If an action fails or produces unexpected results, adjust the strategy for the next iteration of the loop rather than halting.

### 4. Signaling Completion
- **The Marker**: When the high-level task is fully realized and verified, output the exact marker: `TASK_COMPLETE`.
- **Exit Condition**: The loop terminates only when all pending sub-tasks are resolved and the completion marker is issued.

## Core Capabilities

- **Autonomous Decision Making**: Making executive choices on file placement, refactoring paths, and testing strategies.
- **Self-Correction**: Detecting loops or dead-ends and pivoting to alternative solutions.
- **Progressive Refinement**: Starting with a rough prototype and iterating until production quality is reached.

## Usage Instructions

1.  **Load First**: Always prioritize loading this skill at the start of a complex session.
2.  **Iterative Mindset**: Do not attempt to solve everything in one turn. Plan for 3-5 iterations of the Ralph Loop.
3.  **Target Awareness**: Be highly sensitive to "action directories" or "vaults" where pending work is stored. Moving or processing these files is often the primary metric of progress.

## Concrete Example

**User**: "Process all the markdown reports in /Vault/Needs-Action and summarize them."

**FTE-CI Strategy**:
1.  **Iteration 1**: List `/Vault/Needs-Action`. Identify 3 reports.
2.  **Iteration 2**: Read and summarize Report A. Move Report A to `/Vault/Processed`.
3.  **Iteration 3**: Read and summarize Report B. Move Report B to `/Vault/Processed`.
4.  **Iteration 4**: Read and summarize Report C. Move Report C to `/Vault/Processed`.
5.  **Iteration 5**: Verify `/Vault/Needs-Action` is empty. Finalize the combined summary.
6.  **Completion**: Output `TASK_COMPLETE`.
