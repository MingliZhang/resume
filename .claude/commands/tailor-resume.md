Tailor Mike's resume to a specific job description.

## Instructions

The user has provided a job description (either as `$ARGUMENTS` or pasted in the conversation). Use it to tailor the resume as follows:

### Step 1 — Read context
Read these files in parallel:
- `/Users/minglizhang/code/resume/notes.md` — raw experience details and facts
- `/Users/minglizhang/code/resume/CV/experience.tex`
- `/Users/minglizhang/code/resume/CV/skills.tex`
- `/Users/minglizhang/code/resume/CV/summary.tex`
- `/Users/minglizhang/code/resume/CV/education.tex`
- `/Users/minglizhang/code/resume/CV/projects.tex`

### Step 2 — Analyze the job description
Identify:
- The core role (ML, backend, fullstack, infra, etc.)
- Key technologies and tools mentioned
- What the team/company values (scale, research, product, reliability, etc.)
- Seniority signals and what they want candidates to demonstrate

### Step 3 — Tailor experience bullets
For each bullet in `experience.tex` (both active and commented out):
- **Uncomment** bullets that are directly relevant to the JD or demonstrate something the role values
- **Comment out** bullets that are unrelated and would not help Mike stand out for this specific role
- **Add new bullets** if `notes.md` contains relevant experience or details not yet in the resume — draft them in the same style as existing bullets (strong action verb, bolded tech, metric where possible)
- Never delete any bullet — only comment/uncomment

### Step 4 — Tailor skills
- Uncomment or reorder skill rows to surface the most relevant technologies first
- Add any skills mentioned in the JD that Mike has (per notes.md) but are missing from the skills section

### Step 5 — Tailor the objective
- If the current objective doesn't match the role type well, suggest a revised version (comment out the old one, add the new one)

### Step 6 — Compile and verify
Run `xelatex -interaction=nonstopmode resume.tex` from `/Users/minglizhang/code/resume/` and confirm it compiles to 1 page cleanly. If it overflows to 2 pages, ask Mike which bullets to cut rather than deciding unilaterally.

### Step 7 — Report back
Summarize:
- Which bullets were activated and why
- Which bullets were commented out and why
- Any new bullets added
- Whether it fits on 1 page

## Style rules for new bullets
- Lead with a strong action verb (Built, Designed, Architected, Developed, Optimized, etc.)
- Bold key technologies with `\textbf{}`
- Include a metric or outcome where one exists in notes.md
- Keep to 1–2 lines; do not write paragraph-length bullets
- Match the tone and structure of existing active bullets

$ARGUMENTS
