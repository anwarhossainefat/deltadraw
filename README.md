# DeltaDraw: free Theory of Computation toolkit

**Live site:** https://anwarhossainefat.github.io/deltadraw/

DeltaDraw is a free, browser-based companion for a Theory of Computation course. The home page lists the chapters (following Sipser, *Introduction to the Theory of Computation*), and each chapter links to its tools.

## Pages

| Page | What it is | Status |
|---|---|---|
| `index.html` | Home: chapter menu | Live |
| `fa.html` | Ch 1: finite automata (DFA, NFA, ε-NFA) | Live |
| `exam.html` | Exam mode (drawing only, for proctored exams) | Live |
| `regex.html`, `cfg.html`, `pda.html`, `tm.html`, `decide.html`, `complexity.html`, `practice.html` | Later chapters | Planned |

## Finite automata tool (`fa.html`)

The finite automata tool lets you draw DFA, NFA and ε-NFA state diagrams. Draw states and transitions with the mouse, test strings step by step, convert an NFA to a DFA, minimize a DFA, and export a clean diagram as **PNG, SVG, LaTeX (TikZ) or JFLAP (.jff)**. There's nothing to install and no sign-up.

## Features

- Draw states, transitions, curved arrows, self-loops, start arrows and accepting states
- Labels with subscripts (`q_0` → q₀) and symbols (`\epsilon` → ε, `\Sigma` → Σ, …)
- Step-by-step string simulation with highlighted states, plus batch testing
- NFA → DFA conversion (subset construction with ε-closures)
- DFA minimization
- Automatic transition table (copy as Markdown or LaTeX)
- Export to PNG (white or transparent, up to 4×), SVG, LaTeX/TikZ and JFLAP
- Open JFLAP `.jff` files; save and reopen your own drawings (`.json`)
- Auto-save in the browser, undo/redo, zoom and pan, light and dark theme
- Works on desktop and mobile

## How to use

| Action | How |
|---|---|
| Add a state | Double-click empty space, or use the **State** tool |
| Add a transition | `Shift` + drag from one state to another, or use the **Transition** tool |
| Self-loop | `Shift` + drag from a state back onto itself |
| Start arrow | Tick **Initial state**, or `Shift` + drag from empty space onto a state |
| Accepting state | Double-click a state, or tick **Accepting state** |
| Label | Select and type; separate symbols with commas (`0,1`) |
| Curve an arrow | Drag the middle of a transition |
| Delete | `Delete` key or the trash button |
| Undo / redo | `Ctrl+Z` / `Ctrl+Shift+Z` |

## Exam mode

**https://anwarhossainefat.github.io/deltadraw/exam.html** is a drawing-only version for online exams (for example in a Canvas quiz proctored with Honorlock). It doesn't include string testing, NFA → DFA conversion, minimization, the transition table, the DFA/NFA checker, examples or file opening; that code isn't part of the page at all.

- Students start by entering the **exam code** given in the Canvas quiz instructions, plus their name.
- Drawings are saved in the browser **under that code only**. A new code starts with empty questions, and anything untouched for 24 hours is deleted automatically, so nothing can be prepared in advance or carried over between exams.
- Each question number keeps its own drawing.
- **Download answer** saves a PNG named `DeltaDraw_Q<number>_<Name>.png` with the student's name, question number, exam code, the time the drawing was **started** and the time it was **saved** printed at the top. Students upload it to the matching Canvas question.
- The PNG also carries the drawing data, so a grader can open it in the full DeltaDraw (**Open** → choose the PNG) to inspect the exact automaton.

## Run it yourself

DeltaDraw is one self-contained `index.html` file. Download it and double-click to open it in any modern browser, or host it on GitHub Pages.

## Keywords

DFA drawer, NFA drawer, finite automata diagram, automata simulator, state diagram maker, NFA to DFA converter, DFA minimization, finite state machine drawing tool, TikZ automata, JFLAP alternative.
