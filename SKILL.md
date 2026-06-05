---
name: hust-report
description: Draft, revise, and validate HUST-style Chinese lab reports from templates, task books, screenshots, and existing DOCX reports. Use when the user asks to write or modify a Huazhong University of Science and Technology lab report, preserve a provided report template, fix DOCX formatting, repair heading numbering or table/figure captions, update a report directory, or make the writing more formal and template-compliant.
---

# HUST Report

## Core Workflow

Use this skill together with `lab-report-writer` for report content and `documents` for DOCX editing and render/visual QA when those skills are available.

1. Inventory the provided files: template, task book, existing report, screenshots, raw data, rubric, personal information, and previous report examples.
2. Read the template formatting instructions first. If the template includes report-standard pages near the end, read the last three pages carefully before formatting; do not infer body format from the cover or front matter alone.
3. 如果用户提供的模板格式要求与本skill规定的冲突，以用户提供的为准. The user's explicit latest instruction also overrides this skill.
4. Treat the cover, front matter, scoring tables, report requirements, final originality statement/declaration, and other preserved pages as protected template areas. 不要动报告最后面的原创说明 unless the user explicitly requests it.
5. Locate the first body `Heading 1` paragraph and apply report-body formatting only from that point forward. Keep cover/front-matter formatting separate from body-format validation.
6. When screenshots or raw records are numerous, choose representative evidence and explain what the selected evidence covers. Do not paste many near-duplicate images.
7. When content cannot be directly shown or independently tested, state the reason formally and describe the alternative or integrated verification method used.
8. After editing a DOCX, update the table of contents/page numbers, then reapply final OOXML formatting if Word has collapsed run-level font settings.

## DOCX Formatting Rules

Do not globally modify the `Normal` style in an existing report, because it can alter the cover and front matter. Apply styles directly to body paragraphs, heading styles, TOC styles, numbering definitions, captions, and body tables.

For mixed Chinese/English/numeric text, set all font slots explicitly:

- Chinese body text: `w:eastAsia="宋体"`.
- Chinese headings and captions: `w:eastAsia="黑体"`.
- Letters and Arabic numerals: `w:ascii="Times New Roman"` and `w:hAnsi="Times New Roman"`.
- Also set `w:cs="Times New Roman"` unless the template requires otherwise.

If Chinese, digits, letters, punctuation, or symbols have unwanted spaces around them, disable Chinese/English and Chinese/number automatic spacing:

- Set `w:autoSpaceDE` to `0`.
- Set `w:autoSpaceDN` to `0`.
- Apply this at least to TOC entries and body paragraphs.

## Directory Format

- Directory title `目录`: 黑体, 小二, 18 pt, bold, centered.
- Chapter-level TOC entries: 宋体, 小四, 12 pt, bold.
- Other TOC entries: 宋体, 小四, 12 pt, not bold.
- Letters and Arabic numerals in the TOC: Times New Roman, 小四, 12 pt.
- The directory must be a real Word automatic TOC generated from Word TOC fields. Do not create a plain-text/manual directory made only of typed headings, dot leaders, and page numbers.
- Preserve an existing real Word TOC. If the template has no real Word TOC, create one with Word TOC fields rather than manually typing directory entries.
- If the TOC field cannot be safely updated after final formatting, make sure the document still contains the real Word TOC field and that cached TOC page numbers match Word's final page layout.
- Updating a TOC may collapse run-level formatting. Recommended sequence: update TOC/page numbers, reapply final OOXML formatting, then only inspect or render.

## Body Heading Format

- First-level heading: 黑体, 小二, 18 pt, bold, centered. Letters and Arabic numerals: Times New Roman, 18 pt, bold.
- Second-level heading: 黑体, 四号, 14 pt, bold, left aligned. Letters and Arabic numerals: Times New Roman, 14 pt, bold.
- Third- and fourth-level headings: 黑体, 小四, 12 pt, bold. Letters and Arabic numerals: Times New Roman, 12 pt, bold.
- Body text: 宋体, 小四, 12 pt, 1.5 line spacing, standard character spacing.
- Insert page breaks between chapters/first-level headings when the template expects each chapter to begin on a new page. Do not mechanically force every second-level heading to start a new page unless the template says so.
- Use `keep with next` for headings. If a heading would appear alone at the bottom of a page, adjust pagination so the heading and first following paragraph stay together.

## Numbering Rules

Word automatic numbering is formatted separately from heading text. If a heading like `2.2 详细设计` has a number that is smaller or larger than the heading text, modify the numbering definition, not only the paragraph runs.

For `numbering.xml`:

- Match `Heading 1` level numbering to 18 pt, bold, 黑体 for East Asian text, Times New Roman for ASCII/numbers.
- Match `Heading 2` level numbering to 14 pt, bold, 黑体 for East Asian text, Times New Roman for ASCII/numbers.
- Match `Heading 3` and lower levels to 12 pt, bold, 黑体 for East Asian text, Times New Roman for ASCII/numbers.
- Use `w:suff="space"` so the number and heading text have a normal space between them. Headings such as `2.2详细设计` must be corrected to `2.2 详细设计`.

## Tables, Figures, and Screenshots

- Table numbering follows chapter numbering, for example `表2-1`.
- Table titles go above the table.
- Table titles: 黑体, 小四, 12 pt, centered. Letters and Arabic numerals: Times New Roman, 12 pt.
- Table content: 宋体, 五号, 10.5 pt. Letters and Arabic numerals: Times New Roman, 10.5 pt.
- Figure numbering follows chapter numbering, for example `图3-1`.
- Figure titles go below the figure.
- Figure titles: 黑体, 小四, 12 pt, centered. Letters and Arabic numerals: Times New Roman, 12 pt.
- 所有配的图片的解释字都必须要在图片下方居中. Do not put picture explanations above, beside, or floating away from the picture unless the user's template explicitly requires that layout.
- Screenshots should be appropriately sized and readable. Avoid large batches of nearly identical screenshots; use representative images with explanatory analysis.

## Writing Style

- Keep the report formal, objective, and suitable for a university experiment report. Avoid overly colloquial first-person wording such as `我` and `我们` in the report body.
- Prefer expressions such as `本实验`, `该方案`, `该模块`, `该步骤`, `实验结果表明`, `由此可见`, `设计过程中`, `测试过程中`, and `分析可知`.
- Maintain a clear chain of purpose, design idea, implementation method, observed phenomenon, test result, and analysis. Do not merely list screenshots or operation steps.
- 写每一个实验项目的思路、设计、实现、测试和结果分析都要详细一点、丰富一点. Avoid thin one- or two-sentence descriptions for design ideas, module construction, algorithm/process choices, circuit connections, verification steps, or debugging analysis.
- Sections such as `实验总结`, `实验感想`, `意见和建议`, and `问题描述及解决方案` must not be overly brief. Expand them around experiment goals, design thinking, implementation process, test verification, problem handling, improvement direction, and 思政方面 when appropriate.
- For `实验感想`, write from the identity of an undergraduate student majoring in 网络空间安全 when the report context involves that major. The section should normally be 不少于800字, preferably around 1000 Chinese characters. Ideological-political content should account for about 30%-40% and must be closely connected to the experiment, not inserted as generic slogans.
- For `意见和建议`, write 不少于500字 unless the user's template imposes a shorter limit. Tie suggestions closely to the experiment process, course learning, tool/platform experience, verification requirements, documentation standards, and possible improvements.
- If a record, screenshot set, or test material is large, select representative evidence and explain which key cases the selected evidence covers.

## Validation Checklist

Before delivery:

- Confirm the cover and front matter were not changed unless requested.
- Confirm the final originality statement/declaration was not modified unless the user explicitly requested it.
- Confirm the TOC is a real Word automatic TOC field, not a manually typed plain-text directory.
- Confirm the TOC exists and page numbers match the final layout.
- Confirm heading numbers and heading text have matching sizes.
- Confirm heading numbers have a normal following space.
- Confirm body paragraphs use 宋体 小四 12 pt with 1.5 line spacing.
- Confirm first-level chapter headings start on new pages when required and second-level headings are not all forced to new pages.
- Confirm no heading is left alone at the bottom of a page.
- Confirm table captions are above tables and figure captions are below figures.
- Confirm every inserted picture's explanatory text or caption is below the picture and centered.
- Confirm body text contains no colloquial first-person wording.
- Confirm `实验感想` and `意见和建议` meet the requested richness, word-count, professional-identity, ideological-political, and experiment-specific requirements when those sections are present.
- Confirm no raw LaTeX syntax remains in the DOCX.
- Render or open the DOCX for visual inspection whenever possible; structural XML checks alone are not enough for final layout.
