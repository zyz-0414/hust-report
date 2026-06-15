---
name: hust-report
description: Draft, revise, and validate HUST-style Chinese lab reports from templates, task books, screenshots, and existing DOCX reports. Use when the user asks to write or modify a Huazhong University of Science and Technology lab report, preserve a provided report template, fix DOCX formatting, repair heading numbering or table/figure captions, update a report directory, or make the writing more formal and template-compliant.
---

# HUST Report

## Read First

Read this entire `SKILL.md` before acting. It is intentionally compact so the critical formatting rules are not split across many files.

Priority order:

1. The user's latest explicit instruction overrides this skill.
2. The user's provided template or rubric overrides this skill.
3. This skill provides the default HUST-style report workflow and formatting.

Use `lab-report-writer` for content generation and `documents` for DOCX editing/render QA when available.

## Workflow

1. Inventory template, task books, screenshots, raw data, rubrics, personal information, and sample reports.
2. Read the template's formatting instructions first, including the last pages if they contain report standards, originality statements, or preserved tables.
3. Treat cover pages, front matter, scoring tables, report requirements, and originality statements as protected template areas unless the user asks to edit them.
4. Apply report-body formatting only from the first body `Heading 1`; keep cover/front matter formatting separate.
5. Select representative screenshots when evidence is repetitive; explain what the selected evidence proves.
6. After DOCX edits, update TOC/page numbers, then reapply final OOXML formatting because Word often collapses run-level font settings.
7. Render or open the final DOCX for visual QA whenever possible. Do not rely only on XML/text extraction.

## Protected Areas

- Preserve cover layout. When filling cover fields, keep underline fields visible and align comparable underline left/right endpoints.
- Preserve final originality statement/declaration unless explicitly asked to change it.
- Keep the originality heading and declaration body on the same page when the original template does so.
- Do not globally modify `Normal` style in an existing template if doing so would alter protected areas; apply body, heading, TOC, numbering, caption, and table formatting directly or by targeted styles.

## Fonts And Spacing

- Body Chinese: 宋体, 小四, 12 pt, 1.5 line spacing.
- Heading Chinese and caption Chinese: 黑体.
- Letters and Arabic numerals: Times New Roman in `w:ascii`, `w:hAnsi`, and normally `w:cs`.
- Do not leave unintended `等线`/`DengXian` or theme fallback fonts unless the template explicitly requires them.
- Remove unwanted real spaces around Chinese and English/digits/symbols.
- Disable Word automatic Chinese/English and Chinese/number spacing where needed: set `w:autoSpaceDE="0"` and `w:autoSpaceDN="0"` at least for TOC entries and body paragraphs.
- Preserve intentional spaces inside English terms such as `TCP SYN` and normal heading-number spacing such as `2.2 详细设计`.

## TOC

- Use a real Word automatic TOC field. Do not create a manual typed directory.
- Directory title `目录`: 黑体, 小二, 18 pt, bold, centered.
- Chapter-level TOC entries: 宋体, 小四, 12 pt, bold.
- Other TOC entries: 宋体, 小四, 12 pt, not bold, unless the template explicitly requires otherwise.
- Letters and Arabic numerals in TOC entries: Times New Roman, 12 pt.
- Preserve English casing, for example `Scapy` must not become `SCAPY`; remove `caps`/`smallCaps` artifacts.
- Keep TOC entry sizes consistent across the directory page.
- Recommended sequence: update TOC/page numbers, reapply TOC OOXML formatting, then inspect/render.

## Headings And Numbering

- Heading 1: 黑体, 小二, 18 pt, bold, centered; ASCII/numbers Times New Roman 18 pt bold.
- Heading 2: 黑体, 四号, 14 pt, bold, left aligned; ASCII/numbers Times New Roman 14 pt bold.
- Heading 3 and lower: 黑体, 小四, 12 pt, bold; ASCII/numbers Times New Roman 12 pt bold.
- Preserve template heading styles, direct formatting, and numbering links; do not convert headings to plain body text.
- Start first-level chapters on new pages when the template expects it. Do not force every second-level heading onto a new page unless required.
- Use `keep with next` for headings so a heading is not left alone at the page bottom.
- If automatic heading numbers have the wrong size, fix `numbering.xml`, not only paragraph runs.
- Use `w:suff="space"` for heading numbering so `2.2 详细设计` has a normal number-text space; correct forms like `2.2详细设计`.

## Tables, Figures, Screenshots

- Table captions go above tables; figure captions go below figures.
- Table/figure numbering follows chapter numbering, e.g. `表2-1`, `图3-1`.
- Captions: 黑体, 小四, 12 pt, centered; letters/numbers Times New Roman 12 pt.
- Only the caption number such as `表2-1` or `图3-1` is bold. The remaining caption title is not bold unless the template explicitly requires it.
- Table content: 宋体, 五号, 10.5 pt; letters/numbers Times New Roman 10.5 pt.
- Every inserted picture explanation/caption must be below the image and centered.
- Crop long screenshots to the evidence-rich region when full-length insertion would hurt readability.
- Avoid large batches of near-duplicate screenshots; use representative evidence and explain coverage.

## Writing Style

- Write formal, objective Chinese suitable for a university experiment report.
- Avoid colloquial first-person wording such as `我` and `我们`; prefer `本实验`, `该模块`, `实验结果表明`, `分析可知`, etc.
- Avoid meta-report-writing phrasing that should not appear in a student's lab report, such as `做了***，便于报告里***`, `为了在报告中展示***`, or wording that exposes screenshot selection, document assembly, or report-writing convenience. Rewrite these as natural experiment purpose, method, evidence, or result statements.
- Maintain a clear chain: purpose, design idea, implementation method, observed phenomenon, test result, and analysis.
- Do not merely list screenshots or operation steps. Each experiment should include enough design, implementation, testing, result analysis, and problem handling.
- Expand `实验总结`, `实验感想`, `意见和建议`, and `问题描述及解决方案` when present.
- For 网络空间安全 reports, write `实验感想` from the identity of an undergraduate in the major. Prefer at least 800 Chinese characters, with 30%-40% closely connected ideological-political reflection when appropriate.
- For `意见和建议`, prefer at least 500 Chinese characters unless the template imposes a shorter limit.

## Final Checklist

- Protected cover/front matter preserved; filled cover underlines visible and aligned.
- Originality statement preserved as required; heading and body stay on one page when expected.
- Real Word automatic TOC exists; page numbers match final layout.
- Chapter-level TOC entries are bold; other TOC entries are not bold. All TOC entries have consistent 12 pt size, preserve English casing, and contain no `caps`/`smallCaps`.
- Chinese fonts are 宋体 for body, 黑体 for headings/captions; English/digits are Times New Roman; no unintended `等线`/`DengXian`.
- No unwanted Chinese-English/digit/symbol spacing; `w:autoSpaceDE` and `w:autoSpaceDN` disabled where needed.
- Heading numbers and heading text match in size and style; numbering has normal following space.
- Figure/table captions are positioned correctly, centered, use 黑体 for Chinese, and only the number is bold.
- Images are readable, cropped when long, and not repetitive without explanation.
- Body text is formal and not thin; key reflective/advice sections meet requested richness.
- No meta-report-writing phrasing remains, such as statements about doing something merely to make the report easier to write or display.
- No raw LaTeX syntax or placeholder text remains.
- Final DOCX is visually inspected through render/opening; structural checks alone are not enough.
