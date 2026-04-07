---
description: Step-by-step guide for setting up and using Claude Cowork
---

# Claude Cowork Setup & Usage Guide

Quick-reference guide for getting started with Claude Cowork -- Claude Code for non-engineers, built into the Claude Desktop app.

## What is Cowork?

Cowork lets you assign file-based tasks to Claude through a chat interface. You point it at a folder, describe what you want, and Claude reads/modifies files directly. No coding required.

## Requirements

- **Claude Desktop app** (macOS or Windows -- not available on web/mobile)
- **Paid plan:** Pro, Max, Team, or Enterprise
- **macOS:** Apple Silicon (M1 or later)
- Download: https://claude.com/download

## Setup (5 minutes)

### 1. Access Cowork mode
- Open Claude Desktop
- Find the mode selector at the top: **Chat | Cowork | Code**
- Click **Cowork** to enter Tasks mode

### 2. Set up folder access
- Click **"Work in a Folder"** at the bottom of the interface
- Select a local folder -- this is the boundary of what Claude can access
- Grant permissions (read, edit, delete) -- choose "Always Allow" for folders you use often
- **Tip:** Start with a test folder, not your main project directory

### 3. Configure global instructions (optional but recommended)
- Go to **Settings > Cowork > Global Instructions**
- Tell Claude how you work: preferred format, tone, role context
- These apply to every Cowork session automatically

### 4. Give Claude a task
- Type what you need in plain language
- Be outcome-oriented: "Analyze this spreadsheet and summarize spending by category" not "open this file, then copy column B..."
- Claude shows its plan before executing -- review and approve

## Key Features

| Feature | How to use |
|---------|-----------|
| **Folder access** | Click "Work in a Folder" and select a directory |
| **Global instructions** | Settings > Cowork > Edit global instructions |
| **Folder instructions** | Add project-specific context per folder |
| **Plugins** | Settings > Plugins -- add Google Workspace, DocuSign, etc. |
| **Dispatch** | Assign tasks from your phone, Claude works on your desktop |
| **Scheduled tasks** | Type `/schedule` in any task for recurring work |
| **Projects** | Organize related tasks with persistent memory |

## Important Rules

- **Keep the app open** -- closing Claude Desktop kills the session
- **Computer must stay awake** -- sleep stops tasks and scheduled work
- **Review before approving** -- Claude shows its plan first, read it
- **Higher usage than chat** -- batch related work into single sessions
- **Research preview** -- not for regulated workloads (no audit logs, no compliance API)
- **Security:** Claude accesses files you grant -- don't point it at sensitive directories until you're comfortable with how it works

## What Cowork Can Do

- Read, create, and modify files in your designated folder
- Generate formatted documents (Word, Excel, PowerPoint)
- Analyze spreadsheets and produce reports
- Reorganize and rename files
- Multi-step tasks with parallel execution
- Recurring scheduled tasks

## What Cowork Cannot Do

- Work when the desktop app is closed
- Access files outside the designated folder
- Share sessions or artifacts with other users
- Replace regulated/auditable workflows (no compliance logging)

## Troubleshooting

| Problem | Fix |
|---------|-----|
| "Setting up Claude's workspace" message | Normal -- wait for update to complete |
| Task stopped unexpectedly | App was closed or computer went to sleep |
| Hitting usage limits | Batch work into fewer sessions; use Chat for simple questions |
| Missing output files | Check permissions and verify output location |

## Sources

- [Get started with Cowork -- Claude Help Center](https://support.claude.com/en/articles/13345190-get-started-with-cowork)
- [Assign tasks from anywhere -- Claude Help Center](https://support.claude.com/en/articles/13947068-assign-tasks-to-claude-from-anywhere-in-cowork)
