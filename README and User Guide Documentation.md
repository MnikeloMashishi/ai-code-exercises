# README and User Guide Documentation Exercise

# Selected Project

I chose to document the TaskCLI project a command line task management tool for developers. This project has clear features and would be useful for developers who prefer working in the terminal.

# Project Overview

TaskCLI is a lightweight command-line task manager built for developers. It lets you organize and track tasks directly in your terminal, without needing a web interface or heavy GUI apps.

## What TaskCLI Does

TaskCLI makes it easy to manage your tasks from the command line. You can:
- Create and manage tasks
- Organize tasks by projects and tags
- Set priorities and due dates
- Track time spent on tasks
- Receive daily email summaries
- Connect tasks with GitHub issues
- Generate time reports

## Requirements
- Node.js 10+
- npm

# Installation

npm install -g task-cli

# verify the installation:

taskcli --version

# Initial Setup

## Set up preferences:
taskcli init

## Configure your email for notifications:
taskcli config set email your.email@example.com

# Using TaskCLI

## Creating Tasks
taskcli add "Fix login bug"
taskcli add "Write documentation" --due 2024-01-15

## Completing Tasks
taskcli complete 5

# Projects and Tages

## Create a project
taskcli project add "Mobile App"

## Assign tasks to a project
taskcli add "Design login screen" --project "Mobile App"

## Add tags
taskcli add "Fix urgent bug" --tags urgent frontend


# Time tracking

## Start a timer
taskcli timer start 5

## Stop the timer
taskcli timer stop

## See time reports
taskcli report time --from 2024-01-01

# Troubleshooting
- Command not found: Add npm’s global bin folder to your PATH (npm bin -g)
- Email issues: Check your config (taskcli config list) and test email (taskcli email:test)
- Database issues: Reset the database (taskcli db:reset)

# GitHub Integration Guide
## Prerequisites
- TaskCLI installed
- GitHub account
- Repository access

## Steps
1. Get a Personal Access Token on GitHub with repo and read:user permissions.

2. Add token to TaskCLI:
   taskcli config set githubToken your-token

3. Link a project to a GitHub repo:
   taskcli project link "Website Frontend" --repo "username/repo"

4. Connect tasks to GitHub issues:
   - Import issue as task:
     taskcli github import --repo "username/repo" --issue 15
   - Link existing task:
     taskcli link 8 --github-issue 15
   - Sync changes:
     taskcli github sync


# FAQ

## Getting started
Q: What is TaskCLI?
A: A terminal-based task manager for developers.

Q: How do I install it?
A: npm install -g task-cli (requires Node.js).

Q: Do I need terminal experience?
A: Basic commands like cd and ls are enough.

## Working with Tasks
- Create: taskcli add "Do something"
- List: taskcli list
- Complete: taskcli complete 5
- Edit: taskcli update 5 --title "New Title"
- Delete: taskcli delete 5

## Projects & Tags
- Add project: taskcli project add "Website Redesign"
- Assign task: taskcli add "Task" --project "Website Redesign"
- Add tags: taskcli add "Task" --tags urgent backend

## Time Tracking
- Start timer: taskcli timer start 5
- Stop timer: taskcli timer stop
- gAdd time manually: taskcli timer add 5 --minutes 60
- Report: taskcli report time

## GitHub Integration
- Add token: taskcli config set githubToken your-token
- Import issues: taskcli github import --repo "username/repo" --issue 10
- Close GitHub issue with task completion: taskcli complete 5 --push-github

## Common Issues
- Command not found: Ensure npm global bin is in PATH
- Tasks disappeared: taskcli db:reset
- Email not sending: Check your config
- Unsure command: taskcli --help

## Advanced Tips
- Backup tasks: taskcli export --output backup.json
- Import backup: taskcli import backup.json
- Recurring tasks: taskcli add "Weekly report" --recurring weekly