# Task: Generate agent-instructions.md

**Your only task is to create a single file: `agent-instructions.md`**

Do NOT execute any installation or setup tasks. Do NOT create research.md or plan.md. Do NOT perform the three phases described below.

Instead, write a comprehensive instruction document at `agent-instructions.md` that tells a FUTURE AI agent how to perform a complete, from-scratch project installation and setup.

## Instructions for the agent-instructions.md File

The `agent-instructions.md` file you create must describe a three-phase execution model that a future AI agent will follow. Write the file using the following criteria:

### Three-Phase Execution Model (to be documented in agent-instructions.md)

The installation and setup process that you document must instruct the future agent to perform it in three distinct phases, where the future agent must not proceed to the next phase until the user explicitly approves.

### Phase 1: Research (describe this phase in agent-instructions.md)

**Objective**: The future agent must collect all necessary information about the installation and setup requirements.

**Document these tasks in agent-instructions.md**:
1. **Information Gathering**: Analyze the project structure, documentation, configuration files, and dependencies to understand:
   - System requirements and dependencies
   - Environment variables and configuration needs
   - External services or APIs required
   - Database setup requirements
   - Build and deployment processes

2. **Ambiguity Resolution**: Identify any unclear, ambiguous, or missing information that requires user clarification:
   - Missing configuration values
   - Optional vs. required dependencies
   - Platform-specific requirements
   - Version constraints or preferences

3. **Research Documentation**: Create a `research.md` file containing:
   - Summary of findings organized by category
   - List of detected requirements and dependencies
   - Identified ambiguities or questions for the user
   - Recommendations for the installation approach

4. **User Verification**:
   - Present a concise summary of the most important findings
   - Ask the user to review the detailed `research.md` file
   - Request clarification on any ambiguous points
   - **Wait for explicit user approval before proceeding to Phase 2**

### Phase 2: Plan (describe this phase in agent-instructions.md)

**Objective**: The future agent must create a comprehensive, detailed plan for installation and setup.

**Document these tasks in agent-instructions.md**:
1. **Task Breakdown**: Based on approved research, create a detailed task list with:
   - Clear, numbered sequence of all installation steps
   - System package installations
   - Environment variable setup
   - Configuration file creation
   - Database initialization
   - Dependency installation
   - Verification steps

2. **Success Criteria**: For each task, define:
   - **Success Criterion**: What constitutes successful completion
   - **Verification Method**: Specific command or test to verify success
   - **Rollback Strategy**: How to undo the task if needed

3. **Risk Assessment**: Identify:
   - High-risk operations requiring explicit user permission
   - Tasks that modify system configuration
   - Operations that cannot be easily reversed

4. **Plan Documentation**: Create a `plan.md` file containing:
   - Complete numbered task sequence
   - Success criteria and verification methods for each task
   - Permission gates and risk assessments
   - Manual input requirements (consolidated)
   - Execution order and dependencies between tasks

5. **User Verification**:
   - Present a summary of key milestones and critical tasks
   - Ask the user to review the detailed `plan.md` file
   - Highlight any high-risk operations requiring approval
   - **Wait for explicit user approval before proceeding to Phase 3**

### Phase 3: Execute (describe this phase in agent-instructions.md)

**Objective**: The future agent must execute all planned tasks with verification and error handling.

**Document these tasks in agent-instructions.md**:
1. **Pre-execution Checklist**:
   - Confirm all manual inputs are available
   - Verify user has approved the plan
   - Ensure permission gates are understood

2. **Sequential Execution**: For each task in the plan:
   - Display the task name and success criterion
   - Request user permission if task is high-risk
   - Execute the task using specified commands
   - Run the verification method
   - Confirm success before proceeding to next task
   - If verification fails, stop and report to user

3. **Error Handling**:
   - If a task fails verification, **stop execution immediately**
   - Document the failure and what was attempted
   - Present the error to the user with context
   - Ask the user for a decision:
     - Retry with modifications
     - Skip this task
     - Abort the entire installation
   - **Never proceed past a failed task without user approval**

4. **Completion Report**:
   - Summarize all completed tasks
   - List any skipped or failed tasks
   - Verify the overall installation success
   - Provide next steps or usage instructions

## Additional Guidelines for Writing agent-instructions.md

**Remember: You are writing documentation, not executing tasks.**

1. **Numbered Task Sequence**: In the agent-instructions.md file, instruct the future agent to detail every necessary step in order, including system package installations, environment variable setup, and the creation of configuration files.

2. **Automated Detection**: In agent-instructions.md, instruct the future agent to automatically determine values (e.g., OS type, local paths, or versions) whenever possible. If a value cannot be determined automatically, the future agent must prompt the user.

3. **Permission Gates**: In agent-instructions.md, require the future agent to explicitly ask for user permission before executing any installation commands, scripts, or high-risk system modifications.

4. **Manual Input Consolidation**: In agent-instructions.md, instruct the future agent that if multiple manual inputs are required (e.g., API keys, secrets), it should group them into a clear "Manual Input Summary" section in the plan document and write a comprehensive guide human_tasks.md to help the user complete all remaining tasks.

5. **Execution Flow**: Format the agent-instructions.md workflow so a future agent can execute tasks autonomously with minimal human intervention beyond initial permissions and required manual inputs.

6. **Code Readiness**: In agent-instructions.md, provide specific shell commands or scripts that the future agent can execute directly.

## Final Output

After analyzing the project, create a single file: `agent-instructions.md` at the project root. This file should be a complete, standalone instruction set that any AI agent can follow to set up this project from scratch using the three-phase model described above.
