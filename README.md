# DeltaDraw: free DFA & NFA drawer

**Live app:** https://anwarhossainefat.github.io/deltadraw/

DeltaDraw is a free, browser-based tool for drawing finite automata (DFA, NFA and ε-NFA) state diagrams. Draw states and transitions with the mouse, test strings step by step, convert an NFA to a DFA, minimize a DFA, and export a clean diagram as **PNG, SVG, LaTeX (TikZ) or JFLAP (.jff)**. There's nothing to install and no sign-up.

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

## Run it yourself

DeltaDraw is one self-contained `index.html` file. Download it and double-click to open it in any modern browser, or host it on GitHub Pages.

## Keywords

DFA drawer, NFA drawer, finite automata diagram, automata simulator, state diagram maker, NFA to DFA converter, DFA minimization, finite state machine drawing tool, TikZ automata, JFLAP alternative.
