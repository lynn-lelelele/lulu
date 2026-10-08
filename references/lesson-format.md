# Lulu Lesson Format

Use a UTF-8 text file with one record per line. Separate fields with `||`. Keep the primary-language line first and the support-language line second.

## Record Types

```text
# comments and blank lines are ignored
page
title||Primary title||Support title
subtitle||Primary subtitle||Support subtitle
h1||Primary section heading||Support section heading
h2||Primary subsection heading||Support subsection heading
h3||Primary sub-subsection heading||Support sub-subsection heading
p||Primary paragraph or teacher line||Support paragraph
b||Primary bullet||Support bullet
f||Primary formula or display line||Support explanation
q||number||Primary exercise||Support exercise
table||number_of_columns||comma-separated-inch-widths
head||Header column 1||Header column 2
row||Cell 1||Cell 2
```

Use `[[BR]]` inside a table cell when the cell needs a line break. The builder turns it into a real Word line break.

## Pairing Rule

Every non-empty content record must contain both languages. For an English-first bilingual lesson:

```text
p||Good morning. Today we will learn the quadratic formula.||同学们早上好。今天学习二次方程求根公式。
```

The builder renders the primary line in a stronger accent style and the support line immediately below it. Headings, questions, formulas, table headers, and table cells follow the same pairing rule.

## Timing Pattern

A 120-minute lesson usually works well with:

```text
0-5    Opening and diagnostic
5-20   Core concept 1
20-35  Worked example and quick check
35-50  Core concept 2
50-65  Guided practice
65-80  Core concept 3
80-95  Independent practice
95-110 Mixed exam-style work
110-120 Exit ticket and homework
```

The exact sequence should follow the source. Do not force this timing pattern when the subject has a different natural structure.

## Formula Normalization

Author formulas with Unicode mathematical notation. The builder also normalizes common ASCII forms:

| Avoid | Use |
| --- | --- |
| `sqrt(x)` | `√x` |
| `+/-` | `±` |
| `x^2` | `x²` |
| `abs(z)` | `|z|` |
| `pi`, `theta`, `alpha`, `beta` | `π`, `θ`, `α`, `β` |
| `->` | `→` |

Use `z*` for a conjugate when an overline is unavailable. Keep formulas editable as text; do not rasterize them unless the user explicitly requires an image-only equation.

## Quality Checks

- Every exercise has a quick answer and a full solution.
- Every English teacher line has a Chinese support line immediately below it.
- The lesson states what is covered when source content exceeds the requested duration.
- The timing adds up to the requested class length.
- The final document is rendered and checked for split pairs, clipped table cells, missing fonts, and broken math symbols.
- The final response cites only the final artifact, not builder files or QA images.
