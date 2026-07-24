# TryHackMe Standalone Room Documentation Workflow v2.1

_Last Updated: July 2026_

---

# Workflow Overview

This workflow is used for all standalone TryHackMe room collections (e.g., Active Directory, Windows, Linux, SOC, Cloud, etc.). The focus is on learning through hands-on practice while maintaining professional-quality documentation for my Root & Repository portfolio.

Rather than interrupting practical work to create detailed notes after every task, I complete the room first while recording important reminders and documenting meaningful practical work. Once the room is finished, I generate comprehensive notebook notes and repository documentation.

---

# During Every Task

## Step 1 – Explain the Task

Before beginning each task:

- Explain the concept.
- Explain why it matters.
- Define important terminology.
- Explain the real-world relevance.

---

## Step 2 – Quick Notebook Jot Notes

Provide concise reminders to write in my notebook while working through the task.

These should be short bullet points that capture important concepts, commands, or reminders—not full notebook notes.

Example:

- Kerberos uses ticket-based authentication
- OUs organize Active Directory objects
- `Get-ADUser` retrieves user information
- Follow the Principle of Least Privilege

---

## Step 3 – Complete the Task

Work through:

- Questions
- Practical exercises
- Hands-on labs
- Flags
- Troubleshooting

without stopping to generate polished documentation.

---

## Step 4 – Screenshot Guidance

Only request screenshots when documenting meaningful practical work.

### Capture screenshots for:

#### Hands-on Labs

Examples:

- Creating users
- Creating groups
- Creating Organizational Units
- Editing Group Policy
- Running PowerShell commands
- Enumeration
- Exploitation
- Mitigation
- Security tool usage

---

#### Administrative Tasks

Capture work that demonstrates technical ability.

Examples:

- Active Directory Users and Computers
- Group Policy Management
- Windows Administration
- Linux Administration
- Terminal output
- Configuration changes

---

#### Important Results

Examples:

- Flag obtained
- Successful login
- Successful command output
- Successful configuration
- Policy successfully applied
- Verification results

---

#### Errors & Troubleshooting

Errors are valuable learning opportunities and should be documented.

When an error occurs:

1. Capture a screenshot of the error.
2. Troubleshoot the issue together.
3. Capture a screenshot of the successful resolution.
4. Include the troubleshooting process in the final documentation.

Examples:

- Authentication failures
- Permission denied
- Configuration mistakes
- Command errors
- Service failures
- Connection issues

---

### Do NOT capture screenshots for:

- Multiple-choice answers
- Reading-only tasks
- Completed question pages
- Answer submission pages

unless the page contains meaningful technical information worth documenting.

---

# After Completing the Entire Room

Generate documentation in the following order:

## 1. Full Handwritten Notebook Notes

Generate one comprehensive notebook page containing:

- Room overview
- Key concepts
- Important terminology
- Commands used
- Why each concept matters
- Real-world applications
- Practical skills developed
- Troubleshooting performed
- Lessons learned
- Personal takeaways

---

## 2. Screenshot Checklist

Generate a checklist containing only meaningful screenshots collected throughout the room, including:

- Practical labs
- Administrative tasks
- Tool usage
- Errors
- Troubleshooting
- Successful fixes
- Final room completion

---

## 3. Generate `task-notes.md`

Create the room's complete GitHub-ready documentation.

---

## 4. Update the Collection README

Regenerate the full standalone collection `README.md` with all affected sections updated.

---

## 5. Update the Collection Images README

Regenerate the full `images/README.md` with all screenshot references updated.

---

## 6. Update the Parent Standalone Rooms README

Regenerate the full `Standalone-Rooms/README.md` with all affected sections updated, including:

- Collection progress
- Room counts
- Completion percentages
- Current room
- Next room
- Skills developed
- Documentation standards
- Repository status

---

## 7. Update the Parent TryHackMe README

Update the affected sections of the master `TryHackMe/README.md` while preserving all existing content and ensuring consistency with the standalone collection documentation.

---

## 8. Repository Consistency Review

Verify:

- Room status
- Collection progress
- Screenshot totals
- Skills lists
- Repository structure
- Documentation consistency
- Collection README references
- Standalone Rooms README
- Parent TryHackMe README

Ensure all documentation is internally consistent before finalizing.

---

## 9. Git Commands

Generate the exact Git commands:

```bash
git add .
git commit -m "Complete <Room Name> documentation"
git push origin main
```

---

# Repository Structure

```text
Standalone-Rooms/
│
├── README.md
│
├── Collection-Name/
│   ├── README.md
│   ├── images/
│   │   ├── README.md
│   │   └── screenshots
│   │
│   ├── Room-Name-1/
│   │   └── task-notes.md
│   │
│   ├── Room-Name-2/
│   │   └── task-notes.md
│   │
│   └── Room-Name-3/
│       └── task-notes.md
```

---

# Documentation Principles

- Prioritize learning over documentation during labs.
- Keep quick notebook reminders while working.
- Produce comprehensive notebook notes after completing the room.
- Document practical work instead of question completion.
- Capture troubleshooting as part of the learning process.
- Regenerate every affected documentation file in full.
- Perform a documentation consistency audit before finalizing.
- Maintain professional, portfolio-quality documentation.
- Keep repository organization consistent across all standalone collections.