# Visual presentation guide

A rule of thumb: if the solution's argument depends on *where* something is (a point, a
region, a repeating position), draw it. If it only depends on a *value* (an amount, a count),
prose and arithmetic are usually enough. This file covers the recurring cases and gives a
minimal template for each.

## Picking a renderer

Use the richest option the current environment actually supports, in this order of
preference:

1. **A real rendered image or interactive artifact** (an SVG embedded in an artifact/canvas, a
   generated plot via a plotting library, a diagramming tool) — always prefer this when it's
   available, because it's what the student can visually check the algebra against.
2. **Inline SVG in a markdown/HTML response**, if the surface renders it, is a lightweight way
   to get a real figure without extra tooling.
3. **A clearly labeled ASCII sketch** as the fallback when nothing richer is available. It's
   worse than a real diagram, but far better than describing coordinates purely in a sentence
   — a reader can still see relative position and proportion.

Whatever you use, label points and values with the *exact same names* the algebra uses
(`A`, `B`, `R`, `s`, `k`, ...) so the student can move their eyes between the figure and the
proof without translating.

## Geometry and coordinate setups

If a solution says "place `B` at the origin, let the square have side `s`, so `A = (0, s)`,
`C = (s, 0)`, `D = (s, s)`" — draw exactly that, with the given points (`P`, `Q`, `R`, etc.)
and given lengths marked.

Minimal SVG template for a labeled coordinate figure:

```html
<svg viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
  <!-- axes -->
  <line x1="20" y1="280" x2="280" y2="280" stroke="#888"/>
  <line x1="20" y1="280" x2="20" y2="20" stroke="#888"/>
  <!-- square ABCD -->
  <polygon points="20,280 220,280 220,80 20,80" fill="none" stroke="black" stroke-width="2"/>
  <circle cx="20" cy="280" r="3"/><text x="5" y="298">B</text>
  <circle cx="220" cy="280" r="3"/><text x="225" y="298">C</text>
  <circle cx="220" cy="80" r="3"/><text x="225" y="75">D</text>
  <circle cx="20" cy="80" r="3"/><text x="5" y="75">A</text>
  <!-- point P on AD, Q on AB, and segment intersection R -->
  <circle cx="20" cy="150" r="3" fill="red"/><text x="5" y="150">P</text>
  <circle cx="120" cy="80" r="3" fill="red"/><text x="120" y="70">Q</text>
  <line x1="20" y1="280" x2="20" y2="150" stroke="blue"/> <!-- BP -->
  <line x1="220" y1="280" x2="120" y2="80" stroke="green"/> <!-- CQ -->
</svg>
```

Adjust coordinates to the actual problem's proportions — the point is the pattern (axes, the
figure, labeled given points, the segments the proof actually uses), not this specific square.

For a pure ASCII fallback, a labeled sketch beats prose even when it's rough:

```
A(0,s) ------------------- D(s,s)
  |  \                       |
  |    \Q                    |
  |      \                   |
  |        \                 |
  |          \___R           |
  |               \          |
B(0,0) -----------------C(s,0)
```

## Function behavior and bounding regions

When a solution bounds `f` between two lines of a fixed slope (a Lipschitz-type condition, an
interpolation bound), draw the anchor points and the "cone" of allowed values, not just the
inequality:

```
        forbidden (too steep)
              \        /
               \      /
                \    /
   ----k+50------●-------- ceiling for f(x) near an anchor at height k
                 anchor (x0, k)
   ----k-50------●-------- floor
                /      \
               /        \
        forbidden (too steep)
```

Mark the actual anchor coordinates and the actual slope bound from the problem — the value of
this picture is that the student can see *why* the bound is symmetric and where the ± 50 (or
whatever the number is) physically comes from.

## Periodic / modular patterns

When a sequence's digits or a modular quantity repeats with some period, a cycle diagram or a
short table beats a written-out list of "x0=1, x1=1, x2=1, x3=0, ...":

```
k mod 3:   0    1    2
x_k:       0    1    1     (repeats forever)
```

or, for a true cycle (e.g. remainders under repeated squaring):

```
   2 --> 4 --> 1
   ^            |
   +------------+
   (period 3, mod 7)
```

## Algebra

Pure symbol-shuffling (simplifying a rational expression, isolating a variable) usually
doesn't need a picture — but a surprising amount of algebra has a spatial or physical meaning
that's worth surfacing, especially the first time a technique appears:

- **Equations as balance.** `x + 3 = 7` is a balance scale with `x + 3` on one pan and `7` on
  the other; "do the same thing to both sides" is "keep the scale level while you remove
  weight." Useful the first time a student is learning *why* the same-operation-both-sides
  rule works, not just that it works.

  ```
    [ x | 3 ]  ===  [   7   ]        [ x ]  ===  [   4   ]
       balanced                    still balanced after
                                    removing 3 from both pans
  ```

- **Area models for expanding and factoring.** `(x + 2)(x + 3)` as a rectangle split into four
  pieces makes distributing feel geometric instead of like a memorized FOIL rule, and it's the
  same picture used later for factoring in reverse.

  ```
            x        3
        +--------+-------+
      x |  x^2   |  3x   |
        +--------+-------+
      2 |  2x    |  6    |
        +--------+-------+
  ```

- **Number lines for inequalities and absolute value.** `|x - 3| < 5` is "all points within 5
  of 3" — draw the point, the radius, and the resulting interval, rather than only solving it
  algebraically into `-2 < x < 8`.
- **Graphs for roots, intersections, and behavior.** A system of equations is where two lines
  (or curves) cross; a quadratic's roots are where its graph meets the x-axis; an inequality's
  solution set is a shaded region. If a solution's algebra finds these values, plot them too —
  it turns an abstract "solve for x" into something the student can see and sanity-check.
- **When to skip it.** If the manipulation is purely symbolic with no spatial reading (e.g.
  combining like terms, simplifying `\frac{x^2-1}{x-1}`), don't force a diagram — a quick
  numeric check (plug in a value, confirm both sides match) is the better sanity-check tool
  there instead of an unnecessary picture.

## Statistics and combinatorics

Tree diagrams for sequential choices, Venn diagrams for overlapping conditions, and simple
tables for casework are usually enough — these rarely need a full coordinate figure, but
should still be drawn rather than only narrated, since the whole value of these visuals is
letting the student see all branches/cases at once instead of holding them in memory.
