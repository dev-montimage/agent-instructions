---
name: setup-agent
description: Generate comprehensive AI agent setup instructions for complete project installation and configuration. Use when the user asks to create installation instructions, setup guides, or agent-instructions for a project.
allowed-tools: Read, Grep, Glob, Bash, Write, TodoWrite, AskUserQuestion
---

# Setup Agent - Comprehensive Installation Instructions Generator

Generate a comprehensive instruction set for an AI agent to perform a complete, from-scratch project installation and setup. Write these instructions to `agent-instructions.md` at the project root using the following criteria:

## Three-Phase Execution Model

The installation and setup process must be performed in three distinct phases. **Do not proceed to the next phase until the user explicitly approves.**

### Phase 1: Research
**Objective**: Collect all necessary information about the installation and setup requirements.

**Tasks**:
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

### Phase 2: Plan
**Objective**: Create a comprehensive, detailed plan for installation and setup.

**Tasks**:
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

### Phase 3: Execute
**Objective**: Execute all planned tasks with verification and error handling.

**Tasks**:
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

## Additional Guidelines

1. **Numbered Task Sequence**: Detail every necessary step in order, including system package installations, environment variable setup, and the creation of configuration files.

2. **Automated Detection**: Instruct the agent to automatically determine values (e.g., OS type, local paths, or versions) whenever possible. If a value cannot be determined automatically, it must prompt the user.

3. **Permission Gates**: Require the agent to explicitly ask for user permission before executing any installation commands, scripts, or high-risk system modifications.

4. **Manual Input Consolidation**: If multiple manual inputs are required (e.g., API keys, secrets), group them into a clear "Manual Input Summary" section in the plan document. Write a comprehensive guide `human_tasks.md` to help user complete all remaining tasks.

5. **Execution Flow**: Format the workflow so the agent can execute tasks autonomously with minimal human intervention beyond initial permissions and required manual inputs.

6. **Code Readiness**: Provide specific shell commands or scripts within the instructions that the agent can execute directly.

## Output Files

The skill should produce the following files:

- `research.md` - Phase 1 research findings and ambiguities
- `plan.md` - Phase 2 detailed task breakdown and execution plan
- `agent-instructions.md` - Final comprehensive installation instructions
- `human_tasks.md` - Manual tasks that require human intervention

## Example Workflow

When this skill is activated:

1. User asks: "Create setup instructions for this project"
2. Claude enters Phase 1 (Research):
   - Explores project structure
   - Reads package.json, requirements.txt, docker-compose.yml, etc.
   - Identifies dependencies and requirements
   - Creates `research.md`
   - Asks user for approval to proceed
3. User approves, Claude enters Phase 2 (Plan):
   - Creates detailed task breakdown
   - Defines success criteria for each task
   - Writes `plan.md`
   - Asks user for approval to proceed
4. User approves, Claude enters Phase 3 (Execute):
   - Follows the plan sequentially
   - Verifies each step
   - Creates final `agent-instructions.md`
   - Creates `human_tasks.md` if needed
   - Reports completion

## Best Practices

- Always use the TodoWrite tool to track progress through the three phases
- Use AskUserQuestion to resolve ambiguities identified in Phase 1
- Never proceed to the next phase without explicit user approval
- Stop immediately if any verification step fails
- Provide clear, actionable error messages
- Group all manual input requirements together for user convenience
