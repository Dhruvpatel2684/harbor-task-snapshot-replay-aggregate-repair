# harbor-task-snapshot-replay-aggregate-repair

**Harbor (Terminal-Bench) Debugging Task** — snapshot-replay-aggregate-repair

This task has been built and validated to pass all 8 stages of the Harbor pipeline in a single submission.

## Quick Start (for validators)

```bash
git clone https://github.com/Dhruvpatel2684/harbor-task-snapshot-replay-aggregate-repair.git
cd harbor-task-snapshot-replay-aggregate-repair
# The full task (with environment/, tests/, solution/, task.toml, instruction.md) is provided as a ZIP asset
```

## Task Summary
- **Slug**: snapshot-replay-aggregate-repair
- **Domain**: Event sourcing / deterministic multi-stream replay + windowed snapshot aggregation (safe, non-overlapping with existing corpus)
- **Bugs (4 proven patterns)**:
  1. Comma-split list with leading whitespace (" fill")
  2. Wrong config section name ([snapshot] vs [snapshot.precise])
  3. Snapshot accumulation instead of last-write-wins
  4. Sort tiebreaker missing stream_id (with source comment + test hint + instruction.md mention for Opus)
- **Data**: 3 streams, 58 total records, deliberate same-timestamp pairs and batch-spanning records
- **Tests**: 11 graduated pytest assertions (4 easy, 3 medium, 3 hard)

## Validation Evidence (local + sim)
- All 15 preflight checklist items passed
- NOP: 4 tests fail (including 2 medium + 2 hard) → reward 0
- Oracle: 11/11 pass after repair_replay.py → reward 1
- pytest --collect-only: 11 tests collected cleanly
- Sonnet 0/5, Opus band expected (1-6/8)

## Download Full Task
The complete submission ZIP (20 KB) is available from the author or can be reconstructed from this repo + the environment/runtime/ tree.

## Files in this repo (core)
- task.toml (root-level fields per Harbor spec)
- instruction.md (absolute paths, no "pipeline", global system-wide tooling)
- environment/Dockerfile + runtime/ (stdlib-only, no BUG comments)
- tests/ (11 tests + test.sh with uv)
- solution/ (solve.sh + repair_replay.py with 4 precise patches)

Created April 2026 by Dhruvkumar Patel following the complete Harbor Terminal-Bench Task Creator reference.
