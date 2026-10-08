# Lulu

Lulu is a Codex skill for turning supplied teaching material into a ready-to-read bilingual lesson plan. It is designed for requests such as:

- "把这份 PDF 做成 2 小时教案。"
- "英文讲稿为主，每条英文下面配中文。"
- "要有习题、答案、完整解析和可以直接念的 teacher script。"
- "把这份复习资料整理成课堂讲义。"

The default output is an English-first bilingual DOCX with the support language directly below each teaching line. Exercises include a quick answer key and full step-by-step solutions.

## Install

### Windows PowerShell

```powershell
git clone https://github.com/lynn-lelelele/lulu.git "$env:USERPROFILE\.codex\skills\lulu"
```

### macOS or Linux

```bash
git clone https://github.com/lynn-lelelele/lulu.git ~/.codex/skills/lulu
```

Open a new Codex chat after installing so the skill list refreshes.

The DOCX builder requires `python-docx`:

```bash
python -m pip install python-docx
```

## Use

Explicit invocation is the clearest method:

```text
使用 $lulu，把附件 PDF 做成 120 分钟双语教案。英文讲稿为主，每条英文下面必须有一条中文；包含课堂流程、例题、习题、速查答案、完整解析和可直接朗读的 teacher script。输出 DOCX。
```

Other examples:

```text
使用 $lulu，把这份教材页面做成 90 分钟的高中数学教案，保留原书方法，不要补不相关内容。输出 DOCX 和 PDF。
```

```text
使用 $lulu，把附件讲义改成中文为主、英文对照的大学课程教案，并加入 12 道练习和完整解析。
```

## Repository Layout

```text
lulu/
├── SKILL.md
├── README.md
├── agents/openai.yaml
├── references/lesson-format.md
├── scripts/build_bilingual_docx.py
└── assets/icon.svg
```

## Update

```bash
git -C ~/.codex/skills/lulu pull
```

On Windows PowerShell:

```powershell
git -C "$env:USERPROFILE\.codex\skills\lulu" pull
```
