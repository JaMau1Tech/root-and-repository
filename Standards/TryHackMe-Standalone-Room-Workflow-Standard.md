# TryHackMe Standalone Room Documentation Workflow v3.1 (Merged)

_Last Updated: July 2026_

---

# Purpose

This workflow defines the documentation standards for all standalone TryHackMe room collections within the **Root & Repository IT & Cybersecurity Portfolio**.

Unlike structured learning paths, standalone rooms focus on individual technologies, platforms, defensive techniques, offensive techniques, operating systems, cloud services, and enterprise environments.

The purpose of this workflow is to ensure every completed room produces consistent, professional documentation while allowing the learning experience to remain the primary focus.

---

# Documentation Philosophy

The objective of this workflow is **not** simply to document completed rooms.

The objective is to document the engineering process behind completing them.

Learning occurs by:

- Building systems
- Exploring technologies
- Troubleshooting failures
- Recovering from mistakes
- Understanding why solutions work
- Reflecting on the experience

Documentation should demonstrate technical thinking, practical skills, troubleshooting ability, and professional communication — not simply prove a room was completed.

Whenever appropriate, completed documentation should answer the following questions:

- What was built?
- Why was it built?
- What challenges occurred?
- How were those challenges investigated?
- How were they resolved?
- What technical lessons were learned?
- How would this experience be explained during an interview?

The goal is to create documentation that demonstrates engineering thinking rather than tutorial completion.

---

# Workflow Overview

This workflow is divided into two major phases.

## Phase 1 — During the Room

During the room, the focus remains entirely on learning.

Documentation should never interrupt practical work. Instead of producing polished notes after every task, record only short notebook reminders while completing the room.

## Phase 2 — After Completing the Room

Once every task has been completed, generate comprehensive documentation for the repository using the standardized documentation order.

This produces professional documentation while allowing uninterrupted learning throughout the room.

---

# During Every Task

Every task follows the same workflow.

---

## Step 1 — Explain the Task

Before beginning each task:

- Explain the concept.
- Explain why it matters.
- Define important terminology.
- Explain real-world relevance.
- Connect the topic to enterprise environments whenever appropriate.

The explanation should provide enough context that the task makes sense before practical work begins.

---

## Step 2 — Quick Notebook Jot Notes

Instead of generating polished notebook notes after every task, provide concise reminders that can be quickly handwritten while progressing through the room.

Keep these as short bullet points rather than complete notes.

Quick notebook notes should contain:

- Important concepts
- Definitions
- Commands
- Security principles
- Technical reminders

Example:

- Kerberos uses ticket-based authentication
- DNS is critical for Active Directory
- Follow Least Privilege
- SMB Signing protects message integrity
- `Get-ADUser` retrieves user information

The objective is to support learning without interrupting workflow.

---

## Step 3 — Retention Check

Immediately after the jot notes and before hands-on work, ask 1–2 short retention/comprehension questions on the concept just explained.

- Answerable in a sentence or two — active recall, not a quiz.
- Skip for pure navigation/reading tasks with no real concept to check.
- Purpose: confirm the concept is actually being learned, not just documented.

---

## Step 4 — Complete the Task

Work through:

- Questions
- Practical exercises
- Administrative tasks
- Hands-on labs
- Tool usage
- Flags
- Troubleshooting

Do **not** stop after every task to generate polished documentation. The room should be completed naturally before repository documentation begins.

---

# Screenshot Philosophy

Screenshots should document technical work — not room progression. Every screenshot should provide value when viewed independently. The goal is for someone browsing the repository to understand what technical work was performed without reading the room itself.

## Capture Screenshots For

**Administrative Work** — Active Directory Users and Computers, Group Policy Management, DNS Manager, DHCP, Windows/Linux Administration, Azure Portal, AWS Console, VM configuration.

**Hands-on Labs** — creating users/groups/OUs, editing Group Policy, running PowerShell/Bash, enumeration, exploitation, mitigation, security tool usage, packet captures, configuration changes.

**Verification** — successful login, successful command output, policy applied, security configuration enabled, service running, flag obtained, verification results.

**Errors and Troubleshooting** — whenever meaningful troubleshooting occurs:
1. Capture the error.
2. Investigate the problem.
3. Capture the successful resolution.
4. Document the troubleshooting process.

Examples: authentication failures, permission denied, DNS failures, configuration mistakes, service failures, VM issues, connectivity problems, PowerShell errors.

Troubleshooting documentation often demonstrates more technical ability than successful configuration alone — it is considered valuable documentation and should be preserved whenever appropriate.

## Do NOT Capture Screenshots For

Multiple-choice answers, reading-only pages, completed question pages, answer submission pages, progress bars, navigation pages — unless they contain meaningful technical information worth documenting.

---

# Screenshot Naming Standard

Use descriptive, lowercase, hyphen-separated filenames. Do not include file extensions in documentation.

- Task: `room-name-task03-group-policy-created`
- Lab: `room-name-task05-powershell-user-created`
- Troubleshooting: `room-name-authentication-failure` / `room-name-authentication-recovered`
- Completion: `room-name-room-complete`

---

# After Completing the Entire Room

Once every task in the room has been completed, generate the repository documentation in the following order. This order is mandatory and ensures documentation remains organized, consistent, and synchronized across the repository.

---

## Step 1 — Full Handwritten Notebook Notes

Generate one comprehensive set of handwritten notebook notes for the entire room — a complete review suitable for future study (distinct from the quick jot notes taken during the room).

Include:

- **Room Overview** — purpose of the room and technologies explored
- **Key Concepts** — all major concepts introduced
- **Important Terminology** — key technical terms
- **Commands Used** — PowerShell cmdlets, Linux commands, security tool usage
- **Administrative Tasks** — meaningful admin work completed (creating users, editing Group Policy, configuring services/OUs/DNS, reviewing Event Viewer, etc.)
- **Security Concepts** — defensive or offensive concepts covered
- **Troubleshooting Performed** — what failed, symptoms, investigation, resolution
- **Lessons Learned** — most valuable technical lessons
- **Personal Takeaways** — observations that reinforce future learning

---

## Step 2 — Screenshot Checklist

Generate a checklist of only meaningful screenshots collected, organized into logical categories:

- **Administrative Tasks** (Group Policy Management, AD Users and Computers, PowerShell, DNS Manager, etc.)
- **Hands-on Labs** (user creation, configuration changes, security tool usage, successful verification)
- **Troubleshooting** (error screenshots + resolution screenshots)
- **Room Completion** (always include the final room completion screenshot)

---

## Step 3 — Generate `task-notes.md`

Generate the room's complete GitHub-ready documentation, summarizing the room while documenting the engineering work performed. Whenever appropriate, include:

- **Engineering Challenges** — meaningful technical problems encountered (authentication failures, DNS issues, service failures, permission problems, configuration mistakes). If nothing significant occurred, omit rather than forcing one.
- **Troubleshooting Process** — how problems were investigated (Event Viewer, logs, diagnostic commands, connectivity checks, comparing configs, testing hypotheses). Focus on thought process, not just the fix.
- **Resolution** — exactly what fixed it (configuration changes, commands, admin actions, validation steps)
- **Lessons Learned** — technical lessons focused on understanding, not completion
- **Interview Talking Points** — concise summary in this format:
  - **Objective** — what was built or configured?
  - **Challenge** — what technical issue occurred?
  - **Investigation** — how was it diagnosed?
  - **Resolution** — how was it fixed?
  - **Skills Demonstrated** — technical skills practiced

The goal is to transform practical work into an interview-ready story.

---

## Step 4 — Update the Collection README

Regenerate the collection README in full. Never provide partial sections or merge instructions. Update: room status, collection progress, completion percentages, skills developed, repository structure, current focus, next room, documentation references. Ready to immediately replace the existing file.

---

## Step 5 — Update the Collection Images README

Regenerate in full. Update: screenshot inventory, screenshot descriptions, screenshot totals, room completion status. Ensure every screenshot referenced in documentation exists in the checklist.

---

## Step 6 — Update Standalone-Rooms/README.md

Regenerate the parent Standalone Rooms README in full. Update: collection progress, room counts, current room, next room, skills developed, documentation standards, repository status.

---

## Step 7 — Update TryHackMe/README.md

Update the parent TryHackMe README. Preserve all existing content while updating every affected section: standalone room progress, active collection, portfolio statistics, skills gained, current learning focus, repository status. Never overwrite unrelated content.

---

## Step 8 — Repository Consistency Review

Perform a complete documentation audit before finalizing. Review: room completion status, collection progress, completion percentages, screenshot totals, skills lists, repository structure, current/next room, documentation references, README consistency, screenshot references. The assistant is responsible for identifying inconsistencies before presenting documentation.

---

## Step 9 — Git Commands

```bash
git status
git add .
git commit -m "docs(tryhackme): complete <Room Name> room"
git push origin main
```

Alternative commit messages may also be suggested when appropriate. The workflow concludes after the Git commands have been generated.

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

Each collection contains one collection README, one shared images directory, one shared images README, and one `task-notes.md` per completed room. Rooms do **not** contain their own README files or individual images folders.

---

# Documentation Principles

- **Learning Comes First** — never interrupted by excessive documentation; generate polished documentation only after the room is completed.
- **Document Engineering, Not Completion** — document technical work, administrative tasks, configuration changes, troubleshooting, recovery, and lessons learned rather than proving a room was finished.
- **Capture Meaningful Work** — prioritize administrative interfaces, security configurations, command output, verification, errors, troubleshooting, recovery, and final results.
- **Regenerate Every Affected File** — no partial sections, patch notes, merge instructions, or "replace this section" guidance. Every generated file should be immediately ready to replace the existing version.
- **Maintain Repository Consistency** — room counts, collection progress, completion percentages, skills developed, screenshot totals, current/next room, and repository status must all stay synchronized.
- **Document Failures** — the problem, the investigation, the resolution, the lesson learned. Troubleshooting often demonstrates more technical ability than successful configuration alone.
- **Build an Interview Portfolio** — every project should answer: What did you build? Why? What broke? How did you investigate it? How did you fix it? What skills did you demonstrate?

---

# Engineering Mindset

Whenever practical work is performed, approach it using the following engineering lifecycle.

```text
Plan
  ↓
Build
  ↓
Test
  ↓
Break
  ↓
Investigate
  ↓
Recover
  ↓
Document
  ↓
Reflect
  ↓
Interview Story
```

The objective is **not** perfection. The objective is to become proficient at building systems, troubleshooting failures, recovering services, understanding root causes, documenting technical work, and communicating engineering decisions.

---

# Assistant Responsibilities

When assisting with standalone TryHackMe rooms, the assistant will:

- Follow this workflow exactly.
- Prioritize learning over documentation during the room.
- Provide concise notebook jot notes while tasks are being completed.
- Ask 1–2 retention/comprehension questions after each concept explanation, before hands-on work begins.
- Request screenshots only for meaningful technical work.
- Encourage documentation of troubleshooting and recovery.
- Generate comprehensive notebook notes after room completion.
- Regenerate every affected documentation file in full.
- Update all affected README files.
- Perform a documentation consistency audit before finalizing.
- Generate exact Git commands.
- Never fabricate flags, screenshots, labs, or troubleshooting.
- Preserve repository organization and documentation quality.

---

# Version History

## Version 3.1 (Current)

- Merged the full v3.0 philosophy, screenshot naming standard, and post-room documentation sections (Engineering Challenges, Troubleshooting Process, Resolution, Interview Talking Points, Engineering Mindset) with the simplified step structure from the quick-reference version.
- Added a dedicated **Retention Check** step during Phase 1, run after jot notes and before hands-on work on each task.

## Version 3.0

- Introduced an engineering-first documentation philosophy.
- Added dedicated screenshot philosophy.
- Added Engineering Challenges, Troubleshooting Process, Resolution, and Lessons Learned sections.
- Added Interview Talking Points section.
- Added documentation consistency audit.
- Added parent `Standalone-Rooms/README.md` regeneration.
- Introduced Engineering Mindset lifecycle.

---

## Future Changes

Future revisions should be made only after practical use identifies meaningful improvements — evolve the workflow through real experience rather than continual theoretical refinement.

---

**Status:** ✅ Locked

**Current Version:** **v3.1**

**Documentation Standard:** **Official Root & Repository Standalone TryHackMe Workflow**