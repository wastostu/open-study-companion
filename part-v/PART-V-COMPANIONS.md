# Part V companion guide - Investment Planning

These companions accompany Chapter 17 in the separately supplied Part V
print volume. Keep this folder structure intact. The commands below assume
the directory containing this guide and `julia/`.

## Study route

1. Read the [Chapter 17 guide](chapter-17/README.md) and enumerate the four
   EX-3 plans before inspecting the algorithm's suggested build.
2. Run [Benders investment](chapter-17/notebooks/17-benders-investment.ipynb):
   reconcile each master bound, operating bill and supporting cut.
3. Run [two oracles](chapter-17/notebooks/17-two-oracle.ipynb): distinguish a
   valid lower bound from a physically evaluated incumbent, and count setup
   solves as well as the exact phase's solves.
4. Explore the [cut-validity lab](chapter-17/html/cut-validity-lab.html):
   compare exact, relaxed and restricted operating models. Change only the
   line charge to see why an invalid cut can appear harmless in one case and
   select the wrong investment in another.
5. Run [invalid cuts](chapter-17/notebooks/17x-invalid-cuts.ipynb). Predict
   the failure before revealing it. Deliberately invalid models are teaching
   cases; a Julia exception or failed assertion is not an expected success.

The HTML lab is self-contained: open the file in your browser. No Julia
kernel or web server is needed. Its iteration controls replay disclosed
fixed-instance data; they do not solve a general optimization model in the
browser. Local security restrictions may apply; do not disable protections.

## Run the notebooks

The supplied environment records Julia 1.12.7. From this package root:

```text
julia --project=julia
```

At the Julia prompt:

```julia
using Pkg
Pkg.instantiate()
using IJulia
IJulia.installkernel("Part V", "--project=" * dirname(Base.active_project()))
IJulia.jupyterlab(dir=pwd())
```

Initial setup may download dependencies. In JupyterLab select the **Part V**
kernel, restart it, then run all cells from top to bottom. Confirm that
`Base.active_project()` points to this package's `julia/Project.toml`.
Register the kernel again after moving the package: its project path is absolute.

All three experiments contain their Julia implementation inside the notebook;
there is no separate Chapter 17 `.jl` helper or standalone script to launch.
For a script elsewhere explicitly documented as standalone, the general
command is `julia --project=julia path/to/script.jl`. A helper module may
instead require `include(...)` followed by function calls; do not assume
every `.jl` file is a complete application.

Solver ties and timings can differ across platforms. Compare objective values,
validity inequalities and declared tolerances, not incidental tie selections
or identical runtime. Preserve assertion failures and their inputs rather
than deleting checks to complete a run.

## Troubleshooting and evidence

- Missing package: verify the active project, instantiate, restart the kernel.
- Missing kernel or old path: register **Part V** again from this folder.
- Inconsistent output: restart and run all cells in order, without carrying
  variables from a different experiment.
- Suspicious negative gap: reconcile costs, feasibility, probability law and
  bound type before assuming that the last generated cut is the only cause.

Packaged executions must match canonical cell sources and the manifest's
hashes. `evidence/` records the actual accepted execution and plot inspection.
Repository-only `book/`, `tools/`, review files, historical chapter PDFs and
third-party reference PDFs are not dependencies and are not included.

Live HTML rendering, keyboard and assistive-technology acceptance remains
separately blocked by the existing local-HTML restriction. Offline source
and arithmetic checks do not close that gate. The unified book-wide HTML
menu remains a separate end-of-book deliverable.
