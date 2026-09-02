---
name: "Migrate solution to SLNX"
description: "Convert this repository's .sln to the .slnx format and prove nothing broke"
agent: "agent"
argument-hint: "(optional) path to the .sln file; defaults to the one in the workspace root"
---

Convert this solution to .slnx
0. Check the preconditions before touching anything

Run dotnet --version. dotnet sln migrate requires SDK 9.0.200 or later — if this machine is below that, stop and tell me, do not hand-write the .slnx.

Then find everything that names the solution file, because these are what actually break:

CI and CD definitions (.github/workflows/, azure-pipelines.yml, .gitlab-ci.yml)
build and helper scripts (*.ps1, *.sh, *.cmd, Makefile, *.targets)
Dockerfiles
docs and READMEs

List every file and line that mentions the .sln by name. Show me the list before step 1.

1. Record the baseline

Run dotnet sln list and save the project list. Build the solution and save the result. This is what "nothing broke" will be measured against — do not skip it, the comparison in step 4 is the only real verification here.

2. Migrate
dotnet sln <name>.sln migrate

Do not hand-author the XML, and do not delete the .sln yet. Show me the generated .slnx.

If the command refuses because a .slnx of the same name already exists, stop and tell me — someone has migrated this before and the two files may have diverged.

3. Verify the new file describes the same solution

Run dotnet sln <name>.slnx list and diff it against the baseline from step 1. Every project must appear, at the same relative path. Report any difference and stop if there is one.

Then build from the .slnx explicitly and compare against the baseline build.

Pay attention to anything the old file carried that is not just a project list — solution folders, per-project configuration mappings, build-order dependencies, projects deliberately excluded from a configuration. Report anything you cannot account for in the new file rather than assuming the migration handled it.

4. Delete the .sln and update every reference

Only once step 3 is clean. Delete the .sln, and update every file from step 0 to name the .slnx. Leaving both files in place is the actual failure mode: commands run in that directory then need an explicit target and will fail or, worse, silently pick the stale one.

5. Report

Tell me: the SDK version used, whether the project list matched, whether the build matched, every file you edited outside the solution itself, and anything from the old solution file you could not map to the new one.