---
name: lulu
description: "Generate ready-to-read bilingual lesson plans, teacher scripts, exercises, and full solutions from supplied source material such as PDFs, slides, textbook pages, or notes. Use when the user asks for a lesson plan, \u6559\u6848, teaching script, class handout, or a source document converted into a timed class, especially when English-first lines must be paired with Chinese support."
metadata:
  short-description: Generate bilingual lesson plans, teacher scripts, exercises, and solutions
---

# Lulu

Create a teacher-ready lesson from source material. The default output is an English-first bilingual DOCX in which every teaching line is followed immediately by its Chinese support line.

## Default Contract

- Treat the supplied PDF, slide deck, notes, or textbook pages as the content boundary. Do not invent curriculum content or claim that omitted material was taught.
- Infer the student level and subject from the source. Ask for clarification only when duration, target language pair, output format, or assessment level cannot be inferred safely.
- Match the requested duration. If the source contains more than the requested time can cover, build a core lesson and explicitly assign the remaining chapter-review or extension material as homework or later study.
- Produce a lesson with a title, learning outcomes, materials, timed route, board or key-point summary, ready-to-read teacher script, worked examples, exercises, quick answer key, full solutions, and common misconceptions.
- Pair the primary teaching language line with the support language immediately below it. For the common request for English-first teaching plus Chinese support, use English on the first line and Chinese on the next line. Pair headings, questions, answers, table cells, and solution steps too.
- Make the English line speakable. Avoid compressed labels, unexplained symbols, and references to page images that the teacher cannot read aloud naturally.
- Keep exercises below the 60-minute mark modest. As a practical heuristic: about 6-8 teaching blocks and 8-10 exercises for 60 minutes; 10-12 blocks and 12-16 exercises for 120 minutes; 14-18 blocks and 18-24 exercises for 180 minutes. Adjust for the actual cognitive load rather than treating the numbers as fixed.
- Use the user's requested output format. If no format is specified, create DOCX by default because it is easy to edit and print. Produce PDF only when requested or when the environment provides a verified renderer.

## Workflow

1. Read the supplied source completely enough to identify its topics, methods, examples, exercise tiers, and boundaries. For image-only PDFs, render or OCR the pages before writing. Do not rely on a guessed table of contents.
2. Map the source to a timed sequence. State coverage and exclusions explicitly when the source is longer than the requested class.
3. Write the lesson directly into the pipe-delimited format described in `references/lesson-format.md`. Keep the primary-language line and support-language line in the same record.
4. Use `scripts/build_bilingual_docx.py` to create the DOCX. The script keeps each language pair together in one visual pair, reduces split pairs across pages, and normalizes common ASCII math notation.
5. Render the DOCX to PDF or page images when the environment supports it. Check page count, pair integrity, table fit, clipping, and representative pages. Fix source errors and rebuild rather than patching the rendered document.
6. Deliver the final DOCX or PDF. Mention the scope decision only when the source exceeded the requested duration or a requested dependency was unavailable.

## Content Rules

- Write exercises that test the methods actually taught. Include a quick answer key and full reasoning for every exercise.
- Put a common-error correction near the relevant teaching block. State the correct method in the form a student can repeat.
- Keep formulas editable and readable. Use Unicode mathematical notation for radicals, plus-minus, superscripts, Greek letters, absolute value, and implication arrows. Do not leave ASCII spellings such as sqrt, +/-, x^2, abs, pi, or theta in the final output when a readable symbol form is available.
- Prefer short paragraphs and numbered steps in the teacher script. A teacher should be able to read the primary-language line aloud and use the support line immediately below for translation, explanation, or checking.
- Preserve the source's uncertainty and conditions. Do not turn a sample method into a universal theorem, and do not omit caveats such as continuity in a sign-change root test.
- Do not add a bibliography, page-image reproductions, or original-source quotations unless the user asks for them.

## Files

- `references/lesson-format.md` defines the input format, record types, and quality checks.
- `scripts/build_bilingual_docx.py` builds the paired DOCX from a lesson-content file.
- `README.md` contains installation and usage examples for other Codex chats.
