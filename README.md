# DeltaDraw: free Theory of Computation toolkit

**Live site:** https://anwarhossainefat.github.io/deltadraw/

DeltaDraw is a free, browser-based companion for a Theory of Computation course. The home page lists the chapters (following Sipser, *Introduction to the Theory of Computation*), and each chapter links to its tools.

## Pages

| Page | What it is | Status |
|---|---|---|
| `index.html` | Home: chapter menu | Live |
| `fa.html` | Ch 1: finite automata (DFA, NFA, ε-NFA) | Live |
| `regex.html` | Ch 1.3: regular expressions (regex ⇄ NFA, step by step) | Live |
| `pumping.html` | Ch 1.4 and 2.3: the pumping lemma as a proof game (regular and context-free) | Live |
| `cfg.html` | Ch 2.1: context-free grammars (parse trees, CNF, CYK) | Live |
| `pda.html` | Ch 2.2: pushdown automata (draw, run with the stack, grammar → PDA) | Live |
| `tm.html` | Ch 3.1: Turing machines (run on the tape, configurations, formal definition) | Live |
| `decide.html` | Ch 4.1, 4.2, 5.2: deciders, diagonalization, the A_TM proof, PCP puzzle | Live |
| `practice.html` | Chapter 1 practice exercises with exact checking | Live |
| Practice tabs | Chapters 2–3 practice inside `cfg.html` (13), `pda.html` (8) and `tm.html` (7) | Live |
| `exam.html` | Exam mode (drawing only, for proctored exams) | Live |
| `complexity.html` | Chapter 7 | Planned |

## Pumping lemma (`pumping.html`)

A proof game for the pumping lemma for regular languages (Sipser, Theorem 1.70) and for context-free languages (Theorem 2.34). Open `pumping.html#reg` or `pumping.html#cfl` to start in one mode.

- Pick a language (Sipser's Examples 1.73–1.77 and 2.36–2.38, plus languages that *are* regular or context-free).
- The adversary picks p. You type s in terms of p, e.g. `0^p1^p`, `0^(p+1)1^p`, `1^(p^2)`, `a^pb^pc^p`; the page checks s ∈ L and |s| ≥ p.
- The page lists every split the lemma allows, groups them into cases the way Sipser's proofs do ("y has only 0s", "v or y crosses from a's into b's"), and checks whether your i pumps each one out of L. You can choose a different i per case.
- If some split survives every i, the adversary wins with it. When every case is covered, check every p from 3 to 10 and get a proof outline.

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

## Decidability (`decide.html`)

Three tabs (open `decide.html#decidable`, `#undecidable` or `#pcp` directly):

- **Decidable problems (4.1):** a map of Sipser's languages (A_DFA … EQ_TM, ALL_CFG, PCP) marked decidable, Turing-recognizable or neither, with theorem numbers and links to the tools that run them. Run the **E_DFA** decider (marking reachable states), the **EQ_DFA** decider (symmetric difference, with the shortest string where two automata disagree) and the **E_CFG** decider (marking variables round by round). Automata can be typed as text or loaded from your drawing on the finite automata or regular expressions page; grammars can be loaded from the grammars page.
- **Undecidability (4.2):** Cantor's diagonal argument, one digit at a time, and the proof that A_TM is undecidable, following Figures 4.19–4.21 up to the "?" entry for D on ⟨D⟩.
- **Post Correspondence Problem (5.2):** a domino puzzle (click dominoes, see where the rows agree), and a search for the shortest match that says plainly when it has to stop.

## Practice for Chapters 2–3 (Practice tabs)

Open `cfg.html#practice`, `pda.html#practice` or `tm.html#practice`.

- **Grammars (13):** write a CFG for a language (Sipser Exercises 2.4 and 2.6 and more), convert a grammar to Chomsky normal form (Exercise 2.14; the form is checked exactly), and show that a grammar is ambiguous by giving a string with two parse trees (both trees are drawn).
- **Pushdown automata (8)** and **Turing machines (7, deciders that must halt):** each exercise keeps its own drawing on the canvas; **Stop practicing** brings your own drawing back.
- **Check** tests every string up to a length limit and gives the shortest string where the answer and the language disagree, with a button to test it step by step. Equivalence of grammars, PDAs and Turing machines is undecidable, so the page says plainly that the check is bounded.
- Hints one at a time, a solution on request (it doesn't count as solved), and progress saved in the browser.

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

Every page is a self-contained HTML file with no server code: download the files and open `index.html` in a browser, or host them on GitHub Pages.

## Keywords

DFA drawer, NFA drawer, pumping lemma game, PDA simulator, Turing machine simulator, CNF converter, CYK, finite automata diagram, automata simulator, state diagram maker, NFA to DFA converter, DFA minimization, finite state machine drawing tool, TikZ automata, JFLAP alternative.
