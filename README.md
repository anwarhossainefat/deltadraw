# DeltaDraw: free Theory of Computation toolkit

**Live site:** https://anwarhossainefat.github.io/deltadraw/

DeltaDraw is a free, browser-based companion for a Theory of Computation course. The home page lists the chapters (following Sipser, *Introduction to the Theory of Computation*), and each chapter links to its tools.

## Pages

| Page | What it is | Status |
|---|---|---|
| `index.html` | Home: chapter menu | Live |
| `fa.html` | Ch 1: finite automata (DFA, NFA, ε-NFA) | Live |
| `regex.html` | Ch 1.3: regular expressions (regex ⇄ NFA, step by step) | Live |
| `cfg.html` | Ch 2.1: context-free grammars (parse trees, CNF, CYK) | Live |
| `pda.html` | Ch 2.2: pushdown automata (draw, run with the stack, grammar → PDA) | Live |
| `tm.html` | Ch 3.1: Turing machines (run on the tape, configurations, formal definition) | Live |
| `practice.html` | Chapter 1 practice exercises with exact checking | Live |
| `exam.html` | Exam mode (drawing only, for proctored exams) | Live |
| `decide.html`, `complexity.html` | Later chapters | Planned |

## Context-free grammars (`cfg.html`)

- Type a grammar in Sipser's notation, e.g. `S -> 0S1 | ε` (`->` or `→`; `ε` or `\epsilon`; variables are capital letters such as `S`, `S_0`, `A'`, or names like `<EXPR>`). Live feedback lists the variables and terminals and flags variables with no rules, variables that never finish, and unreachable variables.
- **Test a string:** generated or not, with the **parse tree** and the **leftmost derivation** (the simplest one first).
- **Ambiguity:** when a string has two different parse trees, both are drawn and the grammar is marked ambiguous.
- **Chomsky normal form, step by step** (Sipser, Theorem 2.9): new start variable, remove ε-rules, remove unit rules, give terminals their own variables, split long rules. Added rules are green, removed rules are struck out.
- **CYK table**, filled row by row for the tested string.
- **Shortest strings** the grammar generates.

## Pushdown automata (`pda.html`)

- Draw a PDA with Sipser's labels: `a,b→c` reads a, pops b and pushes c (type `->` for the arrow, `ε` or nothing for "none"). Put several rules on one arrow with `;`; they are drawn one per line.
- The stack starts empty, and pushing a string puts its first symbol on top (Sipser's shorthand, e.g. `ε,ε→S$`).
- **Test:** accepted or rejected, decided exactly (also for PDAs whose stack can grow forever). Step through an accepting computation with the input tape, the stack drawn beside it, and the rule in use highlighted on the arrow. The whole computation is listed as a table of configurations.
- **Definition:** the 6-tuple (Q, Σ, Γ, δ, q₀, F) with δ as a table; copy it as Markdown or LaTeX.
- **From grammar:** Sipser's construction (Lemma 2.21) builds a 3-state PDA from any context-free grammar.
- Examples from Sipser (2.14, 2.16, 2.18) and balanced parentheses. Export PNG, SVG, LaTeX (TikZ) or JFLAP; JFLAP `.jff` PDAs can be opened too (JFLAP starts with Z on the stack, DeltaDraw with an empty stack).

## Turing machines (`tm.html`)

- Draw a Turing machine with Sipser's labels: `0→x,R` reads 0, writes x and moves right; `x→R` leaves the symbol as it is; `0,1,x→L` covers several symbols. Use `␣` for blank, `L`/`R` (and `S` to stay, a common variant). Several rules on one arrow are separated by `;`.
- States named `q_accept` / `q_reject` (or drawn as accepting) halt. As in Sipser's diagrams, a missing rule means the machine rejects. The tape is infinite to the right; moving left from the first cell leaves the head in place.
- **Run:** step, play or run to the end, with the tape and head, the rule in use highlighted on the arrow, and Sipser's configurations `u q v` for every step (the trace for Example 3.7 on 0000 matches the book). A machine that repeats a configuration is reported as looping forever; otherwise the run stops at a step limit you choose.
- Nondeterministic machines are explored branch by branch, and an accepting branch is shown.
- **Definition:** the 7-tuple with δ as a table (copy as Markdown or LaTeX).
- Examples: Sipser 3.7 (0 repeated 2ⁿ times), 3.9 (w#w) and a 0ⁿ1ⁿ decider. Export PNG, SVG, LaTeX (TikZ) or JFLAP.

## Practice (`practice.html`)

22 Chapter 1 exercises: DFAs (1.1), NFAs, conversion and minimization (1.2), and regular expressions (1.3).

- **Check answer** compares the answer with the target language exactly. A wrong answer gets the shortest counterexample string, with a button to step through it in the Test tab.
- Rules are checked too: “must be a DFA”, “at most k states”, “as few states as possible”, and only symbols from Σ.
- Hints one at a time, and a solution on request (it doesn't count as solved after the solution is shown).
- Each exercise keeps its own drawing; progress is saved in the browser.
- The practice page hides the Convert, Combine and Regex tools so the answer isn't one click away.

## Regular expressions (`regex.html`)

- Type an expression with `|` or `∪` for union, `*` for star, `ε` or `()` for the empty string, `∅`, and `Σ` for any symbol. `+` can mean union or "one or more" (setting).
- Live feedback shows how the expression is read, or what is wrong with it.
- **Regex → NFA, step by step** (Sipser, Lemma 1.55): one small NFA per piece, joined with ε-moves; parts not built yet are shown faint.
- **NFA → regex, step by step** (Sipser, Lemma 1.60): the drawing becomes a GNFA, then states are removed one at a time, showing R₁(R₂)*R₃ ∪ R₄ with the real labels.
- Test strings, list the shortest strings in the language, and check whether two expressions describe the same language (with the shortest string that tells them apart).

## Finite automata tool (`fa.html`)

The finite automata tool lets you draw DFA, NFA and ε-NFA state diagrams. Draw states and transitions with the mouse, test strings step by step, convert an NFA to a DFA, minimize a DFA, and export a clean diagram as **PNG, SVG, LaTeX (TikZ) or JFLAP (.jff)**. There's nothing to install and no sign-up.

## Features

- Draw states, transitions, curved arrows, self-loops, start arrows and accepting states
- Labels with subscripts (`q_0` → q₀) and symbols (`\epsilon` → ε, `\Sigma` → Σ, …)
- Step-by-step string simulation with highlighted states, plus batch testing
- NFA → DFA conversion (subset construction with ε-closures), with a **step-by-step walkthrough** that fills the subset table one cell at a time and highlights the NFA states involved
- DFA minimization, with a **step-by-step pair table** (table-filling method) showing why each pair is distinguishable
- **Combine** two machines A and B: union, intersection, difference, complement (product construction), and an **equivalence check** that gives the shortest counterexample string
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
