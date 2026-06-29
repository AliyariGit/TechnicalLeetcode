# Architecture — JavaCode Interview Prep

A single-file, zero-dependency web app for Java interview preparation. All logic, styles, and data live in `index.html`.

---

## Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML5 + CSS3 (CSS custom properties for theming) |
| Logic | Vanilla JavaScript (ES6+) |
| Persistence | `localStorage` (solved status, dark/light mode) |
| Syntax highlight | Custom tokenizer (no external lib) |
| Hosting | GitHub Pages — served directly from `index.html` |

---

## File Layout

```
index.html
├── <style>                   CSS variables, components, schema styles
├── <body>
│   ├── .navbar               Top bar — title, theme toggle, search, stats
│   ├── .sidebar              Problem list (difficulty badge, frequency badge)
│   └── .content              Detail panel
│       └── #problem-detail   Rendered per-problem view
└── <script>
    ├── SCHEMAS               Lookup object  { id → HTML string with ASCII diagram }
    ├── PROBLEMS              Array of 35 problem objects
    ├── openProblem()         Renders a problem into #problem-detail
    ├── switchTab()           Tab switcher (Description / Approach / Solution / Schema)
    ├── buildCodeTable()      Line-numbered code renderer with syntax highlighting
    ├── tokenize()            Java tokenizer (keywords, strings, comments, annotations)
    └── localStorage helpers  saveSolved(), loadSolved(), toggleTheme()
```

---

## Problem Object Shape

```javascript
{
  id: 1,
  title: "Two Sum",
  difficulty: "Easy",               // Easy | Medium | Hard
  category: "Array",
  frequency: "★★★★★",              // Mastercard problems only
  mcNote: "...",                    // Mastercard-specific hint (problems 21–35)
  description: "...",               // HTML string
  approach: "...",                  // HTML string (steps + complexity)
  code: [                           // Java solution line-by-line
    "class Solution {",
    "  public int[] twoSum(...) {",
    "    ...",
    "  }",
    "}"
  ]
}
```

---

## SCHEMAS Lookup

`SCHEMAS` is a plain object keyed by problem ID (1–35). Each value is an HTML string containing `.schema-block` divs with `<pre class="schema-art">` ASCII diagrams that visualise the core data structure:

```
SCHEMAS = {
  1:  "<!-- HashMap trace for Two Sum -->",
  2:  "<!-- Stack states for Valid Parentheses -->",
  3:  "<!-- Two-pointer window for Longest Substring -->",
  ...
  35: "<!-- BFS level queue for Word Ladder -->",
}
```

The Schema tab renders `${SCHEMAS[p.id]}` inside the problem detail panel.

---

## Tab System

Each problem panel has four tabs:

```
📋 Description  →  #tab-desc      (problem statement)
💡 Approach     →  #tab-approach  (algorithm steps + Big-O)
☕ Solution     →  #tab-solution  (highlighted Java code)
🗂 Schema       →  #tab-schema    (ASCII data structure diagram)
```

`switchTab(btn, id)` adds `active` class to the clicked button and shows the matching `#tab-{id}` panel.

---

## Syntax Highlighter

`tokenize(line)` splits each Java source line into spans:

| Token type | CSS class | Examples |
|-----------|-----------|---------|
| Keyword | `.kw` | `class`, `return`, `new`, `for` |
| Annotation | `.ann` | `@Override`, `@FunctionalInterface` |
| String/char | `.str` | `"hello"`, `'a'` |
| Number | `.num` | `42`, `3.14` |
| Comment | `.cmt` | `// ...`, `/* ... */` |
| Method call | `.mth` | `map.get(`, `list.add(` |

---

## Theme System

Two CSS themes via a class toggle on `<html>`:

```
default  → dark theme  (--bg1: #0d1117, --blue2: #79c0ff, …)
.light   → light theme (--bg1: #f6f8fa, --blue2: #0969da, …)
```

`localStorage.getItem('theme')` restores the user's last choice on load.

---

## Problem Categories (35 total)

| # | Problems | Category |
|---|---------|---------|
| 1–20 | General Java interview classics | Array, String, DP, Tree, Graph, LinkedList |
| 21–35 | Mastercard SWE2 targeted | Financial logic, Concurrency, System Design |

---

## Deployment

The repo is a single-file static site. Enable GitHub Pages (Settings → Pages → branch: `master` / root) to serve it live at:

```
https://aliyarigit.github.io/TechnicalLeetcode/
```
