# Review and Fix Report

## Changes
- Made the Makefile fail clearly when required `CDE_INCLUDE_PATH` or `CDE_LIBRARY_PATH` is missing, avoiding malformed bare `-I` and invalid `-L/native` commands.
- Fixed constant folding for `<=`.
- Fixed constant folding for `&&`.

## Verification
- `env -u CDE_INCLUDE_PATH -u CDE_LIBRARY_PATH make -n clean` passed.
- `CDE_INCLUDE_PATH=/tmp/cde/include CDE_LIBRARY_PATH=/tmp/cde/lib make -n` emits well-formed include/library flags.
- `git diff --check` passed.

## Remaining
- Full compiler build was not run because real CDE/libkoopa paths are not configured.
- Forward calls to functions defined later remain a larger compiler pipeline issue.
