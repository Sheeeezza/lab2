
#  Code Quality and Refactoring with AI


## Description
A grade-averaging script from an old assignment was critiqued for
modularity, readability and maintainability, refactored, and then
measured with numbers to prove the improvement.

## How to Run
```
python -m pip install pytest
python "Lab 2 Sheeza Rasheed (SP24-BSE-43).py"
```
Expected result: 6 tests pass (3 tests, each run on the old `process()`
and the new refactored code).

## What I Did
1. **Baseline critique:** `process()` did file reading, parsing, grading
   and printing in one function, used single-letter names (d, p, s, a, g),
   buried the grade if/elif chain in a loop, and opened/closed the file by hand.
2. **Fixes applied:** split into `load_records`, `parse_scores`,
   `calculate_average`, `letter_grade`, `build_report`, `print_report`;
   used `with open`; changed bare `except` to `except ValueError`.
3. **Suggestions rejected:** renaming the loop variable `x` (3-line loop),
   removing the `verbose` parameter (could break callers), replacing
   `round(a, 2)` with f-strings (not a bottleneck).

## Measurements (ruff and radon)
| Metric                        | Before | After |
|-------------------------------|--------|-------|
| ruff violations               | 2      | 0     |
| longest function (lines)      | 41     | 10    |
| highest cyclomatic complexity | 15 (C) | 3 (A) |
| parameters on worst function  | 6      | 2     |
| number of functions           | 1      | 6     |

Total lines went up (41 to 50) because of extra `def` and blank lines,
so shorter code was not the goal.

## Behaviour Check
The same 3 tests run against the old and new code:
- sorted by average
- letter grades correct
- bad line skipped

All 6 passed. These tests check returned data only, so they would not
catch a change in `print_report` output.

## Evidence
- Commit hash of baseline: `<paste from git log --oneline>`
- `git diff --stat <before> <after>`: `<paste output>`
- Pytest output: `<paste screenshot or text showing 6 passed>`










<img width="1066" height="787" alt="LAB2" src="https://github.com/user-attachments/assets/479b1208-2451-4010-a97b-e1b324872d06" />



<img width="1066" height="787" alt="LAB2" src="https://github.com/user-attachments/assets/e50c5428-3747-4b7e-9e51-2b134b952e3e" />
