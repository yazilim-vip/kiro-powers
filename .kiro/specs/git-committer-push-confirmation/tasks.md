# Implementation Plan: Git Committer Push Confirmation

## Overview

Update the git-committer power's steering file and documentation to include a mandatory push confirmation step after every commit. This is a documentation/steering-only change — no runtime code is involved.

## Tasks

- [x] 1. Update steering file with push confirmation step
  - [x] 1.1 Add step 7 "Push Confirmation" to the "Workflow for Creating Commits" section in `powers/git-committer/steering/conventional-commits.md`
    - Add the step after step 6 (Add Footers)
    - Include instructions for the agent to always ask the user whether to push
    - Include the confirm path: execute `git push`
    - Include the decline path: inform user the commit stays local
    - Include the error path: display push error and note the commit was created successfully
    - _Requirements: 1.1, 1.2, 1.3, 1.4, 2.1_

- [x] 2. Update POWER.md documentation
  - [x] 2.1 Add push confirmation to the Features list in `powers/git-committer/POWER.md`
    - Add a bullet describing the push confirmation behavior
    - _Requirements: 2.2_
  - [x] 2.2 Add a "Push Confirmation" section to `powers/git-committer/POWER.md`
    - Describe the behavior: always asks after commit, supports confirm/decline/error
    - Place it after the "Breaking Changes" section
    - _Requirements: 1.1, 1.2, 1.3, 1.4, 2.2_

- [x] 3. Final checkpoint
  - Review both files for consistency and completeness
  - Ensure the steering workflow step numbers are sequential
  - Ensure POWER.md and steering file descriptions align
  - Ensure all tests pass, ask the user if questions arise.
