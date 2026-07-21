---
name: vault-project-builder
description: Standardizes the creation of new project spaces in the Obsidian vault (Inputs, Process, Outputs, Feedback folders) and bootstraps a project-specific GEMINI.md file. Can also analyze an existing codebase to initialize its vault representation.
---

# Vault Project Builder Skill

This skill allows the agent to automatically initialize, structure, and bootstrap a standardized project organization system inside the user's Obsidian vault.

## 📁 Standardized Folder Architecture
Every project space created with this skill must contain the following subfolders:
1. **Inputs/**: Raw notes, web clips, research, ideas, and meeting transcripts.
2. **Process/**: Active drafts, working notes, and agent task logs.
3. **Outputs/**: Finished work ready to publish, ship, or send.
4. **Feedback/**: Metrics, audience responses, reviews, and post-mortems.

## 📋 Execution Steps

### Mode A: Creating a New Project Space from Scratch
When requested to create a new project vault:
1. **Gather Details / Interview:** Ask the user for the project name and any available details. Specifically inquire about:
   - What the project is.
   - The primary goals.
   - The target tech stack and deployment (if applicable).
   - Any specific integration or automated inputs/outputs desired.
2. **Create Structure:** Initialize the directories by writing empty placeholder files (e.g., `.gitkeep`) inside:
   - `<Project Name>/Inputs/.gitkeep`
   - `<Project Name>/Process/.gitkeep`
   - `<Project Name>/Outputs/.gitkeep`
   - `<Project Name>/Feedback/.gitkeep`
3. **Write `GEMINI.md`:** Create a `GEMINI.md` at the root of the project folder:
   - Document the project's purpose and primary goals.
   - Outline the folder structure mapping specific to this project.
   - Specify the technical strategy, dependencies, and deployment path.
   - Clarify the agent's specific role (Antigravity's role) in helping achieve the project goals.

### Mode B: Bootstrapping from an Existing Workspace/Code Directory
When the user wants to link an existing code repository or project directory to their Obsidian vault:
1. **Scan Directory:** Read and analyze the existing project workspace files (such as `pyproject.toml`, `package.json`, source files, etc.) using `list_dir` or code research tools to understand:
   - The tech stack.
   - The system architecture.
   - The active files.
2. **Replicate Vault Structure:** Create the project folder in the Obsidian vault with the standard `Inputs/`, `Process/`, `Outputs/`, and `Feedback/` directories.
3. **Generate Custom `GEMINI.md`:** Write a detailed `GEMINI.md` in the new folder based on your analysis of the codebase, outlining:
   - The current architecture and technologies detected.
   - Suggested workflows mapping to the 4 folders (e.g., putting agent task logs in `Process/`, finished build artifacts or docs in `Outputs/`).
   - Your proposed role in assisting with code extensions, refactoring, and testing.
