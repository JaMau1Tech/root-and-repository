# TryHackMe Documentation Workflow

**Version:** 2.0

**Status:** 🔒 LOCKED

**Last Updated:** 2026-07-14

This document defines the official TryHackMe documentation workflow used throughout the Root & Repository project.

No changes may be made without explicit user approval.

---

# Purpose

This workflow ensures every completed TryHackMe room is documented consistently to build:

- Strong technical documentation habits
- High-quality GitHub portfolio projects
- Long-term knowledge retention
- Professional cybersecurity documentation

---

# Standard TryHackMe Room Workflow

Every standard TryHackMe room follows this exact process.

## During Every Task

For **every task** in the room, the assistant must:

### 1. Explain the Task

Provide a concise explanation of:

- What the concept is
- Why it matters
- Important terminology
- Real-world cybersecurity relevance

---

### 2. Generate Handwritten Notebook Notes

Generate ultra-concise handwritten notebook notes using the exact established Module 06 notebook style.

The notes must:

- Use compact bullet points and separators
- Be easy to handwrite
- Include only essential information
- Follow the exact established layout and style
- Never revert to older notebook templates
- Never contain unnecessary paragraphs
- Never change format without explicit user approval

---

### 3. Complete the Task

Provide:

- Correct answers
- Lab guidance
- Flag verification (when applicable)

Never fabricate answers or flags.

---

### 4. Screenshot

Immediately after completing the task:

Tell the user to capture a screenshot.

Provide the exact filename inside its own code block.

Example:

```text
room-name-task01-example
```

No file extensions.

---

### 5. Repeat

Repeat Steps 1–4 for every task until the room is complete.

---

# Lab Workflow

Whenever a room contains a practical exercise or lab:

After completing the lab:

- Verify the flag (if applicable)
- Confirm successful completion
- Prompt for the lab screenshot

Provide the exact filename.

Example:

```text
room-name-task03-firewall-lab
```

---

# Room Completion

After the final task:

Prompt for a room completion screenshot.

Example:

```text
room-name-room-complete
```

---

# After Every Standard Room

Generate documentation in this exact order:

1. Complete handwritten notebook notes
2. Screenshot checklist containing every task screenshot, every lab screenshot, and the final room-completion screenshot
3. Full `task-notes.md`
4. FULL regenerated Module `README.md`
5. FULL regenerated Module `images/README.md`
6. FULL regenerated parent TryHackMe `README.md`
7. Repository structure review
8. Git add / commit / push commands

Before presenting the documentation:

- Regenerate every affected documentation file in full.
- Perform the Documentation Consistency Audit.
- Verify all regenerated files are internally consistent.
- Ensure every file is ready to replace the existing version without requiring manual edits.

---

# Screenshot Naming Standard

Task

```text
room-name-task01-description
```

Lab

```text
room-name-task03-lab-description
```

Room Completion

```text
room-name-room-complete
```

No file extensions.

Use lowercase.

Separate words with hyphens.

---

# Module Repository Structure

```text
Module-XX-Module-Name/
│
├── README.md
│
├── images/
│   ├── README.md
│   └── all screenshots
│
├── Room-Name-1/
│   └── task-notes.md
│
├── Room-Name-2/
│   └── task-notes.md
│
└── Topic-Transition-Recap/
    └── task-notes.md
```

Each module has:

- One README
- One images folder
- One images README

Rooms do **not** contain their own README or images folder.

---

# Topic Transition Recap Workflow

Topic Transition Recap rooms are **module reviews**, not standard learning rooms.

They follow a simplified workflow.

## During the Recap

The assistant should:

- Explain each question
- Generate concise notebook notes
- Provide the correct answer

No screenshot prompts are required.

No room completion screenshot is required.

---

# After Every Topic Transition Recap

Generate documentation in this exact order:

1. Simplified recap `task-notes.md`
2. FULL regenerated Module `README.md`
3. FULL regenerated Module `images/README.md` with no recap screenshots
4. FULL regenerated parent TryHackMe `README.md`
5. Repository structure review
6. Git add / commit / push commands

Before presenting the documentation:

- Regenerate every affected documentation file in full.
- Perform the Documentation Consistency Audit.
- Verify all regenerated files are internally consistent.
- Ensure every file is ready to replace the existing version without requiring manual edits.

---

# Topic Transition Recap Template

```markdown
# Topic Transition Recap

## Status

✅ Completed

---

## Overview

...

---

## Topics Reviewed

...

---

## Key Concepts Learned

...

---

## Skills Developed

...

---

## Personal Reflection

...

---

## Module Summary

### Completed Topics

...

### Skills Gained

...

---

## Next Steps

...
```

---

# Topic Transition Recap Screenshot Policy

No screenshots are required.

Do not generate:

- Question screenshots
- Lab screenshots
- Room completion screenshot

The recap is documented through its summary instead.

---

# Full Documentation Regeneration Standard

After every completed standard TryHackMe room, the assistant must regenerate **all affected documentation files** in full.

The assistant must **never** provide:

- Partial sections
- Patch notes
- "Add this section" instructions
- Merge instructions
- Isolated updates requiring manual editing

Instead, every affected file must be regenerated completely so it can directly replace the previous version.

This includes, but is not limited to:

1. `task-notes.md`
2. Module `README.md`
3. Module `images/README.md`
4. Parent TryHackMe `README.md`
5. Any additional documentation affected by the completed room

Every regenerated file must reflect the current repository state.

The assistant is responsible for ensuring the documentation is complete, current, and internally consistent.

---

# Documentation Consistency Audit

Before presenting any documentation, the assistant must perform a complete documentation consistency audit.

Every regenerated file must agree on:

- Module number
- Module name
- Room statuses
- Completed room counts
- Remaining room counts
- Module progress percentages
- Screenshot filenames
- Screenshot totals
- Skills learned
- Repository structure
- Current learning focus
- Next room
- Overall TryHackMe statistics
- Module status
- Any other information affected by the completed room

If any inconsistency exists, the assistant must correct it before presenting the documentation.

The user should never have to manually reconcile documentation differences.

---

# Assistant Responsibilities

The assistant must:

- Follow this workflow exactly.
- Never skip workflow steps.
- Never change the documentation order.
- Never invent labs.
- Never invent flags.
- Never invent screenshots.
- Keep notebook notes concise.
- Keep GitHub documentation professional.
- Keep repository organization consistent.
- Treat Topic Transition Recaps differently from standard rooms.

No workflow modifications may be made without explicit user approval.