# JavaCode — LeetCode-Style Java Interview Prep

A single-file, zero-dependency web app for Java interview preparation. Browse 35 problems, read the algorithm walkthrough, view syntax-highlighted Java solutions, and study ASCII data-structure diagrams — all in one page.

🔗 **Live app:** [aliyarigit.github.io/TechnicalLeetcode](https://aliyarigit.github.io/TechnicalLeetcode/)

---

## Features

- **35 problems** — general Java interview classics + Mastercard SWE2 targeted questions
- **4 tabs per problem** — Description · Approach · Solution · Schema
- **Syntax-highlighted Java** — keywords, types, strings, annotations, comments
- **ASCII data-structure diagrams** — visualise the core algorithm for every problem
- **Dark / Light theme** — persisted in localStorage
- **Search & filter** — by title, tag, or difficulty (Easy / Medium / Hard)
- **Mark as Solved** — progress tracked in localStorage
- **Copy button** — copies raw Java code to clipboard
- **Zero dependencies** — one HTML file, no build step, no CDN

---

## Problem List

| # | Title | Difficulty | Category |
|---|-------|-----------|---------|
| 1 | Two Sum | Easy | Array / HashMap |
| 2 | Valid Parentheses | Easy | Stack |
| 3 | Maximum Subarray | Easy | DP / Kadane |
| 4 | Climbing Stairs | Easy | DP |
| 5 | Merge Two Sorted Lists | Easy | LinkedList |
| 6 | Binary Search | Easy | Divide & Conquer |
| 7 | Reverse Linked List | Easy | LinkedList |
| 8 | Linked List Cycle | Easy | Floyd's Cycle |
| 9 | Longest Substring Without Repeating | Medium | Sliding Window |
| 10 | Validate Binary Search Tree | Medium | Tree / DFS |
| 11 | Number of Islands | Medium | BFS / DFS |
| 12 | Coin Change | Medium | DP |
| 13 | Product of Array Except Self | Medium | Prefix/Suffix |
| 14 | LRU Cache | Medium | HashMap + DLL |
| 15 | Course Schedule | Medium | Topological Sort |
| 16 | Find Median from Data Stream | Hard | Two Heaps |
| 17 | Sliding Window Maximum | Hard | Monotonic Deque |
| 18 | Longest Common Subsequence | Medium | DP (2D) |
| 19 | Unique Paths | Medium | DP (2D) |
| 20 | Word Search II | Hard | Trie + Backtracking |
| 21–35 | Mastercard SWE2 Questions | Mixed | Financial / System Design |

---

## Mastercard SWE2 Topics (Problems 21–35)

Luhn Algorithm · Bucket Sort · Top K Frequent · Minimum Window Substring · Word Ladder · Serialize/Deserialize BST · Kth Largest · Trapping Rain Water · Jump Game II · Meeting Rooms II · Merge Intervals · Task Scheduler · Basic Calculator · Expression Add Operators · Minimum Cost to Connect Sticks

---

## Architecture

See [`architecture.md`](architecture.md) for a full breakdown of the app structure, data shapes, tab system, and syntax highlighter.

### Quick overview

```
index.html
├── <style>          CSS variables, dark/light themes, schema styles
├── <body>
│   ├── .navbar      Title, theme toggle, search, stats
│   ├── .sidebar     Problem list (difficulty, frequency badges)
│   └── .content     Per-problem detail panel
└── <script>
    ├── SCHEMAS      { id → HTML ASCII diagram }  (35 entries)
    ├── PROBLEMS     Array of 35 problem objects
    ├── openProblem  Renders problem into detail panel
    ├── switchTab    Tab switcher
    ├── buildCodeTable  Line-numbered code renderer
    └── highlight    Java tokenizer → syntax-coloured HTML
```

---

## Running Locally

No build step needed — just open the file:

```bash
# Clone
git clone https://github.com/AliyariGit/TechnicalLeetcode.git
cd TechnicalLeetcode

# Open in browser
start index.html        # Windows
open index.html         # macOS
xdg-open index.html     # Linux
```

---

## Enabling GitHub Pages

1. Go to **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: **master** / **/ (root)**
4. Save — the live URL appears at the top of the Pages settings

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML5 + CSS3 |
| Logic | Vanilla JavaScript (ES6+) |
| Persistence | `localStorage` |
| Hosting | GitHub Pages |

---

## License

MIT
