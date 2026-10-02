# Part I companion guide — Chapters 1–5

Use each guided notebook after its chapter, then run the matching experiment
notebook. These are original Julia teaching sources, not exercises to paste into
one shared session. HTML widgets are self-contained and can be opened directly in
a browser; no server or Julia kernel is required for them.

## Setup — start from the directory containing this guide

The same layout is used in the source repository and the distributed companion
package: `julia/` sits beside `chapter-01/` through `chapter-05/`.
Use Julia 1.12.7 for the recorded environment. Start a terminal **here**, not inside
an individual chapter, and run:

```text
julia --project=julia
```

At the Julia prompt:

```julia
using Pkg
Pkg.instantiate()
using IJulia
IJulia.installkernel("Part I", "--project=" * dirname(Base.active_project()))
IJulia.jupyterlab(dir=pwd())
```

The first installation may download packages and require network access. If
JupyterLab is not installed, follow IJulia's setup prompt or use an existing
Jupyter installation. Select the **Part I** Julia kernel for each notebook, then
**Restart Kernel and Run All Cells**. The registered kernel contains the absolute
project path: register it again if this directory moves. A fresh kernel prevents
variables from another notebook from changing the lesson's results.

The distribution contains freshly executed notebook outputs. Timings, MIP node
counts and solver choices among equivalent optima can differ on another machine.
Assertions check the lesson's mathematical invariants, not identical timings.

## Study routes

| Chapter | Guide | Main lesson | Experiment |
|---|---|---|---|
| 1 | [Linear algebra](chapter-01/README.md) | [Guided notebook](chapter-01/notebooks/01-linear-algebra.ipynb) | [Conditioning](chapter-01/notebooks/01x-illconditioning.ipynb) |
| 2 | [Linear programming](chapter-02/README.md) | [Simplex](chapter-02/notebooks/02-simplex.ipynb) | [Degeneracy](chapter-02/notebooks/02x-degeneracy.ipynb) |
| 3 | [Duality](chapter-03/README.md) | [Duality](chapter-03/notebooks/03-duality.ipynb) | [Duals at kinks](chapter-03/notebooks/03x-degenerate-duals.ipynb) |
| 4 | [Integer programming](chapter-04/README.md) | [Branch-and-bound](chapter-04/notebooks/04-branch-and-bound.ipynb) | [Big-M](chapter-04/notebooks/04x-bigM.ipynb) |
| 5 | [Network flow](chapter-05/README.md) | [Network flows](chapter-05/notebooks/05-network-flows.ipynb) | [Loop flow](chapter-05/notebooks/05x-loopflow.ipynb) |

## Supporting experiments

Run from the same root directory:

```text
julia --project=julia chapter-02/notebooks/review2-experiments.jl
julia --project=julia chapter-03/solutions/basis_certificate.jl
julia --project=julia chapter-04/review2-experiments.jl
```

Chapter 2 measures row scaling and damped Newton behavior; unavailable internal
solver timings are not inferred. Chapter 3 checks an equality/nonnegative LP basis
certificate. Chapter 4 measures formulation performance and two heuristics; the
default experiment does not guarantee a timeout or a pump cycle.

## Book and later chapters

The current print volume is named `part-i-foundations-of-optimization.pdf` in the
`output/pdf` directory of the source workspace (or the sibling `pdf` directory
when companions are distributed inside `output`). It contains all printed
exercises and solutions. Old standalone chapter PDFs are not the current edition.
Pointers to Chapters 6–17 identify later volumes, which are not included here.

The root distribution README and repair ledger state the latest acceptance
status. Passing Julia/JavaScript tests alone does not certify browser layout or
assistive-technology behavior. Reference PDFs are supporting library copies;
check their permissions before redistributing them outside your study workspace.
