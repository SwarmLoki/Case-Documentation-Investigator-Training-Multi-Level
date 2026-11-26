# Case-Documentation-Investigator-Training-Multi-Level
Case Documentation Investigator Training — Multi-Level
# Case Documentation Investigator Training — Multi-Level

A self-contained, browser-based training simulation for **law enforcement officers** and **child-welfare investigators**. Trainees work through realistic — but entirely fictionalized — investigative scenarios, identify documentation failures, and practice better questioning, evidence handling, and reporting.

No installation. No backend. No external dependencies. One HTML file.

---

## What It Is

The tool presents **11 scenario modules** built from the kinds of documentation gaps that commonly appear in real investigative files: paraphrased child disclosures, unverified self-reported alibis, normal medical exams misread as proof of no abuse, unsearched evidence, unreferenced chain-of-custody, and children present during violence but never interviewed.

Each module follows the same rhythm:

1. **Scenario Briefing** — the trainee reads the case record as the original investigator would have received it.
2. **Your Investigation** — the trainee answers multiple-choice, short-answer, branch, and prioritization questions based **only** on the text provided.
3. **Debrief** — the trainee reviews exactly what the original investigation missed and the key takeaway.

A standalone **Report Audit / Redline Lab** adds a practical exam where trainees flag flawed sentences, score the report against a four-dimension rubric, and draft a corrected supplemental narrative.

---

## Quick Start

```bash
# Clone
git clone https://github.com/SwarmLoki/Case-Documentation-Investigator-Training-Multi-Level.git
cd Case-Documentation-Investigator-Training-Multi-Level

# Open in any modern browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

No server, build step, or dependency install is required.

> **Filename note:** The current HTML file is named `deepseek_html_20261125_40acbc(2).html`. Parentheses in filenames break some static hosts and LMS importers. **Rename or copy it to `index.html` before deployment.**

---

## Features

| Feature | Description |
|---|---|
| **11 scenario modules** | Redacted, fictional case files covering child disclosures, daycare allegations, medical findings, drug investigations, domestic violence, and verification gaps. |
| **Foundation / Field-Senior modes** | Foundation shows Key Facts up front and full explanations. Field / Senior hides Key Facts until completion, defers explanations, and adds prioritization and consequence prompts. |
| **Branch questions** | Wrong investigative moves surface their downstream consequence (contamination, lost evidence, inadmissible seizure). |
| **Prioritization questions** | Trainees rank competing actions (safety vs. preservation vs. coordination) with uniqueness validation. |
| **Self-check rubrics** | Writing prompts include a checklist of qualities to verify before submission. |
| **Report Audit / Redline Lab** | Standalone practical: click-to-flag flawed sentences, score against a 4-dimension rubric, draft a corrected narrative. |
| **Local progress** | Answers, mode, revealed model answers, and audit state persist in `localStorage` across refreshes. |
| **Print / Copy / Export** | Per-module and audit summaries can be printed, saved as PDF, or copied to clipboard for LMS paste-in. |
| **Mobile-first** | Sticky mobile bar with drawer navigation, `100dvh` sizing, and scroll containment. |
| **Safe reset** | Two-click confirm that works inside iframes and webviews where `confirm()` is blocked. |

---

## Trainee Modes

### Foundation
- Key Facts visible before answering.
- Full explanation shown after each answer.
- Best for new investigators, onboarding, or refresher training.

### Field / Senior
- Key Facts hidden until the module is completed.
- Explanations deferred until completion.
- Adds branch consequences and prioritization constraints.
- Best for experienced investigators, supervisory review, or pre/post-course assessment.

Mode is selectable from the home screen and the sidebar, and persists across sessions.

---

## Module Index

| # | Title | Focus |
|---|---|---|
| 1 | The Disclosure | Child forensic interview fundamentals |
| 2 | The Parent Contact | Engaging the non-offending caregiver |
| 3 | The Daycare Report | Initial response in a child-care setting |
| 4 | The Husband | Interviewing a household member with potential access |
| 5 | The Provider | Interviewing the child-care provider |
| 6 | The Medical Exam | Reading and using medical findings |
| 7 | The Drug House | Child safety in a drug/alcohol investigation |
| 8 | The Offense Report | Evidence, chain of custody, follow-through |
| 9 | The Domestic Arrest | Children present during domestic violence |
| 10 | The Contradiction Matrix | Organizing conflicting statements |
| 11 | The Background Interview | Verification and context in child welfare |

---

## Report Audit / Redline Lab

A standalone practical exam, reachable from the home screen or sidebar without completing the 11-module sequence.

**Step 1 — Flag Flaws.** Click any sentence in the flawed report to flag it. Each flagged sentence reveals its specific deficiency.

**Step 2 — Score the Report.** Rate the report on four 25-point dimensions:

- **Facts & Quotes** — names, dates, times, verbatim statements, source attribution
- **Evidence & Chain of Custody** — items, packaging, serial numbers, sealing, lab submissions
- **Child Safety & Referrals** — DHS notification, medical exam, safety plan, forensic interview
- **Verification & Follow-Up** — independent corroboration, records requests, pending actions

**Step 3 — Draft the Corrected Narrative.** Write a corrected supplemental report, then check off the self-check rubric before revealing the model key.

**Step 4 — Compare.** Reveal the model audit key and compare flags, scores, and corrected narrative side-by-side.

---

## Exporting Summaries

Each module and the Audit Lab include two export options:

- **🖨 Print / Export Summary** — opens the browser print dialog with a clean, print-styled summary showing trainee answers, correct answers, and outcomes. Print to PDF or send directly to a printer.
- **📋 Copy Summary** — copies the same summary to the clipboard as plain text, ready to paste into an LMS assignment, email, or case-management note.

Summaries include the trainee's mode, timestamp, per-question selections and results, and the module's key lesson.

---

## Repository Structure

```
.
├── README.md                                       ← this file
├── index.html                                      ← recommended name for the training app
└── deepseek_html_20261125_40acbc(2).html           ← current filename (rename to index.html)
```

**Recommended cleanup before publication:**

1. `cp 'deepseek_html_20261125_40acbc(2).html' index.html`
2. Optionally keep the original filename as an archive copy, or delete it once `index.html` is verified.
3. Add an empty `.nojekyll` file at the repo root (prevents GitHub Pages from running the file through Jekyll).
4. Add a `LICENSE` file (see License section below).

---

## Deployment

### Option A — Open Locally

Best for individual training or testing. Double-click `index.html` or run `open index.html` from the terminal.

### Option B — GitHub Pages (recommended for distribution)

1. Rename the HTML file to `index.html`.
2. Add an empty `.nojekyll` file to the repo root.
3. Commit and push.
4. In GitHub: **Settings → Pages → Source: `main` branch, root directory**.
5. Your live URL will be `https://swarmloki.github.io/Case-Documentation-Investigator-Training-Multi-Level/`.

Free, HTTPS-enabled, no tracking. Best for sharing a link with colleagues or embedding in an internal wiki.

### Option C — SCORM Package (future)

For LMS-based completion tracking (Schoology, Moodle, Canvas), the app would need:

- A `SCORM_API` bridge that writes `cmi.core.lesson_status` and `cmi.core.score.raw` on module completion.
- An `imsmanifest.xml` at the root of a ZIP package.
- Testing in SCORM Cloud before upload.

This is **not yet implemented** in the current build. The tool works standalone today; SCORM reporting would be a follow-on enhancement.

---

## Customizing

The entire training dataset lives in the `MODULES` and `AUDIT_LAB` constants near the top of the `<script>` block. Each module is a self-contained object:

```js
{
  id: 1,
  title: "The Disclosure",
  subtitle: "Child Forensic Interview Fundamentals",
  intro: "…",
  briefing: ["…", "…"],
  keyFacts: ["…", "…"],
  questions: [
    { type: "mc", q: "…", options: ["…","…","…","…"], correct: 1, explain: "…" },
    { type: "text", q: "…", model: "…", selfCheck: ["…","…"] },
    { type: "branch", q: "…", options: [{ text: "…", correct: true, consequence: "…" }] },
    { type: "priority", q: "…", items: ["…"], order: [0,1,2,3], explain: "…" }
  ],
  missed: ["…", "…"],
  lesson: "…"
}
```

To add a new module, copy an existing object, assign a new `id`, and update the `MODULES` array. No other changes are required — navigation, progress tracking, and export all derive from the array.

To change the color scheme, edit the CSS custom properties in `:root` at the top of `<style>`.

---

## Disclaimer

> ⚠️ **All names, places, dates, agencies, and details in this training are fictional composites created for instructional purposes.** They do not represent any real person, case, or jurisdiction. Any resemblance to real events is coincidental.
>
> The scenarios are derived from *patterns* of documentation failure commonly observed in investigative practice. They are not transcriptions of any specific case.
>
> This module is intended for **authorized professional training use only**. It is not a substitute for jurisdiction-specific law, policy, supervision, legal review, or clinical judgment.

---

## License

There is currently **no license** on this repository. Before redistributing, publishing, or accepting external contributions, choose one explicitly.

Common choices for a training tool of this kind:

- **MIT** — maximum reuse; simplest; appropriate if you want the code freely adaptable.
- **CC BY-NC 4.0** — attribution + non-commercial; appropriate if you want to keep the content out of commercial training vendors.
- **CC BY 4.0** — attribution only; permissive for training and adaptation.

Add a `LICENSE` file at the repo root with the full text of your chosen license, and replace this section with a one-line reference (e.g., "Licensed under the MIT License — see `LICENSE`.").

---

## Contributing

Issues and pull requests are welcome. When contributing:

- Do **not** add real names, real addresses, or re-identifiable combinations.
- Keep all training content fictional and composite.
- If adding a new module, follow the existing object schema and include a `missed` list and `lesson` summary.
- Test in Foundation **and** Field / Senior mode before submitting.

---

## Acknowledgments

Built as a self-contained HTML training tool for practitioners who train other practitioners. Module content reflects widely documented investigative and child-welfare documentation standards, not any single agency's policy.
