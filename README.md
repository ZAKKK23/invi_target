# plane-moving-targets 

A Voronoi Tessellation Population (VTP) agent simulation with moving targets —
a MATLAB model and a dependency-light browser port of the same dynamics.
Targets here move in **aligned** straight lines / a sine wave, as opposed to
the Tusi-couple oscillator or independent-bouncing variants of this project.

**[Live site →](#)** (enable GitHub Pages, see below)

## What it is

Agents ("cells") move under three local forces computed from their Delaunay
neighborhood:

- **repulsion** from the nearest neighboring agent
- **alignment** toward neighbors heading the same direction
- **homing** toward whichever target is currently closest

Each step is capped by an estimate of the agent's own Voronoi cell size, so a
crowded agent can never leap past its neighbors. Two constants shape that
balance and are live-editable on the *live simulation* tab (and in the MATLAB
control panel):

- **&nu;** — alignment strength (weight of the alignment force relative to
  repulsion + homing)
- **L** — interaction length scale (sets the distance at which repulsion/
  homing hand off, and caps how far a crowded agent can move per step)

### Target motion

You choose a number of **straight-line targets** (0–5). Each one travels
along its own fixed-height horizontal line — several parallel lanes. One more
target is always added on top of those: it moves **sinusoidally in y**
(its own height/amplitude/&omega; parameters) while still moving horizontally
like everything else, so it traces a wavy path.

Every target — including the oscillating one — shares a **single** horizontal
speed and a **single** shared x-coordinate. There's only one `x(t)` in the
whole system; each target differs only in `y(t)`. That means every target is
aligned (exactly the same x) at every instant, not merely at the start.




