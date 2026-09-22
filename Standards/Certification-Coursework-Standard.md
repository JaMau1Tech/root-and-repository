# Certification Coursework Standard

**Version:** 1.0

**Status:** 🔒 LOCKED

**Last Updated:** 2026-09-22

This document defines the official standard for documenting **certification coursework** (CompTIA A+, Network+, Security+, CySA+, etc.) throughout the Root & Repository project.

This standard applies to structured, exam-driven coursework delivered by module/lesson (CertMaster, Schoology, instructor slides). It does **not** replace Notebook-Standards.md, which governs hands-on lab rooms (TryHackMe, home-lab builds) — those stay on the existing handwritten/screenshot-driven format. Coursework has a different shape: no lab to screenshot for "explain PCIe lane widths," and the retention need is memorized facts + exam-trap recognition, not a hands-on record.

No changes may be made without explicit user approval.

---

# Core Principles

- Notes prioritize genuine understanding over memorized bullets — a plain-language explanation of *why* sits under every dense fact.
- Two files per module serve two different review speeds: **Study Notes** (fast, lesson-numbered, scan-and-recall) and **Objectives** (slow, in-depth prose, cross-referenced to the official CompTIA objective codes — not just the instructor's/Schoology's numbering, which is not guaranteed to match).
- Every module also produces a **Practice Questions** file — this is where actual retention gets tested, not just documented.
- Nothing is invented: no fabricated lab results, no CertMaster content that wasn't actually pasted in, no quiz scores that weren't actually earned. A module's status must clearly reflect what's real vs. still pending.
- Exam traps and common misconceptions get flagged explicitly (⚠) wherever they occur — these are exactly what separates a passing score from a missed question on scenario-heavy exams like A+.

---

# File Set Per Module

Every completed module produces three files, plus matching `.docx` printable copies of each:

1. `module-##-study-notes.md` (+ `.docx`)
2. `module-##-objectives.md` (+ `.docx`)
3. `module-##-practice-questions.md` (+ `.docx`, optional — .md is the primary working copy)

---

# STUDY NOTES — Required Structure

- **H1** — Module number + title (matches the official CertMaster/course module title)
- Italic subtitle line — cert + domain (e.g. *CompTIA A+ Core 1 (220-1201)*)
- One line naming which CompTIA objective codes the module covers, and its % weight on the real exam where known
- **H2** per lesson section (`N.N — Title`), **H3** per sub-lesson (`N.N.N — Title`), matching the source numbering exactly as given (Schoology/CertMaster), even when it diverges from CompTIA's own numbering — the divergence itself gets a one-line note if it's confirmed to exist for that module
- Condensed bullets under each sub-lesson — facts, specs, and the one-line "why," not full paragraphs
- ⚠ flags on exam traps, easily-confused pairs, and common wrong answers
- A **Quick Self-Check** (before any real quiz data exists) or **Quiz & Review Key Takeaways** (once real lesson-review/quiz results come in) section at the end of each module, or folded in per-lesson if that's how the scores actually arrived

---

# OBJECTIVES — Required Structure

- **H1** — Module number + "Objectives — In-Depth"
- Organized by **official CompTIA objective code** (e.g. `3.1 — Compare and contrast display components and attributes`), not by lesson number — this is the cross-reference layer that catches cases where Schoology's numbering doesn't match CompTIA's real domain structure
- In-depth prose per objective — full explanations, analogies, real-world framing, not bullet lists (Study Notes already covers the condensed version)
- **Learning Outcomes** section at the end — explicit Q&A, each stated learning outcome from the course restated as a question with a full-prose answer beneath it

---

# PRACTICE QUESTIONS — Required Structure (NEW)

This is the retention-testing layer that was previously missing.

- **H1** — Module number + "Practice Questions"
- Questions organized by lesson/objective, matching the module's own numbering
- Every question includes:
  - The question stem (scenario-style where the real exam is scenario-style)
  - All answer options, not just the correct one
  - The correct answer, with a **why** explanation grounded in the module's own notes
  - For every wrong option: a short **why it's wrong** — what it's confusing, or what would have to be true for it to be the right answer instead
- Questions drawn from: (a) real quiz/lesson-review questions already logged in Study Notes, expanded with full option-by-option reasoning, and (b) new application-style questions built from confirmed note content — never from outside/invented technical claims
- A running **Missed-Concept Watchlist** at the bottom — concepts that caused an actual wrong answer on a real graded quiz/checkpoint, carried forward until they stop being missed

---

# Docx / Print Formatting

- ROOT & REPOSITORY branding header
- Courier New monospace for headers
- Black-and-white, printable, unless the specific assignment calls for color
- Docx mirrors the Markdown 1:1 — Markdown is the source of truth (git-tracked); docx is the generated printable copy, regenerated in full on any update, never hand-diverged from it

---

# Writing Standards

Use:
- Plain-language explanations under dense facts (💡-style, matching existing established notes)
- Exam-trap callouts (⚠) wherever a concept is a known point of confusion
- Full prose in Objectives; condensed bullets in Study Notes — don't blur the two

Avoid:
- Copying CertMaster/instructor material verbatim beyond what's needed to reference it
- Inventing quiz scores, lab results, or lesson content that wasn't actually provided
- Letting Practice Questions duplicate Study Notes as trivia recall only — they should test the reasoning, not just the fact

---

# Assistant Responsibilities

The assistant must:
- Keep Study Notes, Objectives, and Practice Questions as three distinct files serving three distinct purposes — never collapse them into one.
- Cross-reference the real CompTIA objective codes, flagging any confirmed mismatch with the course's own numbering.
- Never invent quiz results, scores, lab content, or completed work.
- Regenerate the full file on any update (never a partial silent edit that leaves the docx out of sync with the Markdown).
- Keep the Missed-Concept Watchlist current as real quiz/checkpoint results come in.
- Never change this structure without explicit user approval once this standard is locked.
