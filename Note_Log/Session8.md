## Session 8 June 17, Wednesday

### What I did
- Started FAILURE_ANALYSIS.md wrote Overview section and Pipeline Assumptions vs Environment Reality table
- Identified four core assumption categories: lane marking contrast, lighting conditions, urban edge clutter, road boundary visibility
- Sharpened table content to reference specific mechanisms from earlier sessions hysteresis chaining onto building edges, headlight blowout creating false gradients rather than generic "noise" language
- Ran a full codebase review using Copilot against main.py, folder structure, and session logs
- Identified and fixed two robustness issues: missing isOpened() checks on both VideoCapture objects, missing slope guard in make_line() to prevent divide-by-zero or near-zero slope crashes

### Key takeaways from code review
- Core pipeline logic and research framing are sound failure is environmental, not a misuse of OpenCV
- Missing: README.md, requirements.txt, consistent file naming, completed FAILURE_ANALYSIS.md
- Several review points (quantitative metrics, related work citations) are valid in general but intentionally deferred qualitative analysis was a deliberate choice given no ground truth labels exist
- Confirmed roadmap: finish FAILURE_ANALYSIS.md next, then adaptations phase, then polish phase (README, cleanup)

