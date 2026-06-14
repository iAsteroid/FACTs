# Power Electronics Notes Skill

A reasoning agent skill for generating publication-ready study notes in LaTeX for power electronics topics. Designed for use with **Reasonix** (and compatible with any Markdown-based AI assistant).

## What it does

This skill provides a **three-stage workflow** with an optional deep derivation mode:

1. **Stage 1: Interactive Chinese Discussion** — Deep, conversational explanation in Chinese to build understanding before writing. Uses physical analogies, cause-effect chains, and invites questions.

2. **Stage 1.5: Deep Derivation Mode** *(optional)* — Step-by-step algebraic derivation with physical meaning after every step. Includes FACT visualization, edge-case questioning, numerical sanity checks, and comparative derivation across topologies.

3. **Stage 2: English LaTeX Notes** — Complete, compilable `.tex` file with professional formatting, `tikz` block diagrams, and a table of contents.

4. **Stage 3: Chinese LaTeX Notes** — Translated version using `ctexart` with `fontset=mac` for XeLaTeX/LuaLaTeX compilation.

## Content Scope

Not limited to any single textbook. Works with:
- Textbooks (Erickson, Mohan, Basso, Kazimierczuk, etc.)
- IEEE/IET academic papers
- Application notes (TI, Infineon, ROHM, STMicro, etc.)
- Course materials, lab manuals, datasheets

## Key Features

| Feature | Description |
|---------|-------------|
| **Formula numbering** | Equation numbers match the original source document for easy cross-referencing |
| **Table of contents** | Auto-generated TOC in every `.tex` file |
| **Block diagrams** | Control loop block diagrams auto-generated with `tikz` |
| **Circuit/waveform figures** | User provides their own; `figbox` placeholders mark insertion points with figure number only |
| **Output organization** | Notes saved in `<source>_notes` subfolder (e.g., `Chapter4_Buck-Boost_notes/`) |
| **Clean compilation** | Auxiliary files (`.aux`, `.log`, `.out`, `.toc`) auto-cleaned after build |
| **Source extraction** | PDF text is extracted before analysis; no content is fabricated |

## Installation

Clone this repo into your `.reasonix/skills/` directory:

```bash
# Global (all projects) — requires write access to ~/.reasonix/
git clone https://github.com/iAsteroid/FACTs.git ~/.reasonix/skills/power-electronics-notes

# Project-level (single project)
git clone https://github.com/iAsteroid/FACTs.git .reasonix/skills/power-electronics-notes
```

Or register as a path in your project's `reasonix.toml`:

```toml
[skills]
paths = [".reasonix/skills/power-electronics-notes"]
```

## Usage

The skill triggers automatically when you:
- Upload textbook pages and ask for notes
- Mention converter topologies (buck, boost, flyback, DAB, LLC, etc.)
- Say "generate notes", "Stage 1/2/3", "笔记", "帮我整理"
- Request formula derivation: "推导这个公式", "每一步都写出来"

Or invoke manually by referencing the three-stage workflow in your message.

## LaTeX Templates

Both templates (.tex files) include:
- `noteblue` color scheme with `\blue{}` command for key insights
- `keybox` environment for fundamental principles and equation summaries
- `figbox` environment for user-provided figure placeholders
- `tikz` + `\usetikzlibrary{positioning}` for block diagrams
- `fancyhdr` professional headers/footers
- `\tableofcontents` with auto-generated TOC
- Numbered equations with `\boxed{}` for critical results

**Chinese template** uses `\documentclass[11pt, a4paper, fontset=mac]{ctexart}` — compatible with TeX Live on macOS.

## Output Files

```
<source>_notes/
├── main_en.tex    (English notes, compile with pdfLaTeX)
├── main_en.pdf
├── main_cn.tex    (Chinese notes, compile with XeLaTeX/LuaLaTeX)
└── main_cn.pdf
```

## Author

Study Notes By **Asteroid**

---

## 中文说明

一个用于生成电力电子学 LaTeX 学习笔记的 AI skill（适用于 Reasonix 等智能助手）。

### 三阶段工作流

1. **Stage 1：中文互动讨论** — 先用中文深入讲解，物理类比+因果链+递进式推导，构建理解后再动笔
2. **Stage 1.5：公式推导模式** *(可选)* — 不跳步推导，每步解释物理含义，FACT 可视化，极端条件验证
3. **Stage 2：英文 LaTeX 笔记** — 完整可编译 `.tex` 文件，含 tikz 控制框图和目录
4. **Stage 3：中文 LaTeX 笔记** — 翻译为中文版，公式编号与原书一致

### 核心特性

| 特性 | 说明 |
|------|------|
| **公式编号** | 与原文档保持一致，便于对照 |
| **自动目录** | 每份笔记自带 `\tableofcontents` |
| **控制框图** | 用 `tikz` 自动生成 |
| **电路/波形图** | 由用户自行绘制插入，仅留图号占位 |
| **输出结构** | 保存在 `<资料名>_notes` 子文件夹 |
| **编译清理** | 自动删除 `.aux` `.log` `.out` 等中间文件 |
| **内容提取** | PDF 文本先提取再分析，不编造内容 |

### 安装方法

```bash
git clone https://github.com/iAsteroid/FACTs.git .reasonix/skills/power-electronics-notes
```

或在 `reasonix.toml` 中注册路径。

### 使用方式

Skill 会在以下情况自动触发：
- 上传教材页面并要求生成笔记
- 提到变换器拓扑（buck、boost、flyback、DAB、LLC 等）
- 说 "generate notes"、"Stage 1/2/3"、"笔记"、"帮我整理"
- 要求公式推导："推导这个公式"、"每一步都写出来"

### 输出文件

```
ChapterX_xxx_notes/
├── main_en.tex    (英文笔记，pdfLaTeX 编译)
├── main_en.pdf
├── main_cn.tex    (中文笔记，XeLaTeX/LuaLaTeX 编译)
└── main_cn.pdf
```
