# SDDP companion — Binder pilot

Prepared 2026-10-01. This is a pilot, not a passed online-runtime release.
Published to the author's public repository with their authorization.
The companion is free and the books will never be sold.

Only the two representative notebooks are included:

- `part-i/chapter-01/notebooks/01x-illconditioning.ipynb`
- `part-v/chapter-17/notebooks/17-benders-investment.ipynb`

The `.binder` directory pins Julia 1.12.7 and the accepted package versions.
`postBuild` installs an explicitly project-bound IJulia kernel with headless
plotting and one Julia thread. Select **SDDP pilot**, then restart and run all.
The copied part guides describe full local packages, not this minimal pilot;
use the companion website's complete downloads for local execution.

Before enabling any public launch button:

1. Publish this directory alone to the authorized public companion repository.
   Do not upload the book workspace, review evidence or third-party references.
2. Mark `.binder/postBuild` executable in Git.
3. Build with current repo2docker/Binder on Linux. Verify Julia version, active
   project and kernel environment; record the immutable repository commit.
4. Execute both notebooks from fresh kernels, check all assertions, confirm
   plots, and record peak memory and launch time. Local Windows execution does
   not substitute for this check.
5. Test downloading a modified notebook and document temporary-session limits.
6. Only then configure the website with the public repository and pinned commit.

The repository contains the prepared pilot only. No successful Binder build or
online notebook execution is claimed yet.

## Publishing the prepared files

Extract `binder-pilot.zip` into a new, separate directory. Create an empty public
GitHub repository under your own account. From the extracted directory—not the
book workspace—run the commands below. Replace `YOUR-REPOSITORY-URL` with the
HTTPS URL GitHub gives you; do not paste the placeholder unchanged.

```text
git init -b main
git add .binder part-i part-v README.md
git update-index --chmod=+x .binder/postBuild
git commit -m "Prepare SDDP Binder pilot"
git remote add origin YOUR-REPOSITORY-URL
git push -u origin main
```

Share the resulting repository URL with the book's platform maintainer. The
next step is the Binder build and execution check, not enabling an untested link.

Configuration reference:
https://repo2docker.readthedocs.io/en/latest/configuration/research/
Service limits:
https://mybinder.readthedocs.io/en/latest/about/user-guidelines.html
