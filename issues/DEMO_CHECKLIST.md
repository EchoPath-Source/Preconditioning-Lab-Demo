# Demo — Checklist Issue

Source: GitHub Copilot Chat Assistant

This is the single tracker issue for Preconditioning-Lab-Demo. Use this to track the minimal checklist items required to make the public demo a polished, user-facing artifact. Keep implementation details in PRs and close this issue when the high-level items are complete.

Checklist
- [ ] Add client-side JSON/JSONL schema validation and clear error UI
- [ ] Make canvas responsive and support window resize + high-DPI scaling
- [ ] Add built-in sample selector with descriptive names
- [ ] Implement two-way highlighting (card → canvas and canvas → card)
- [ ] Add “Download correlated results” export
- [ ] Add mock kernel-adapter demo mode (shows before/after metrics)
- [ ] Enforce file size limits and friendly messages for large files
- [ ] Add brief guided help/legend and one-paragraph value proposition

Acceptance: each item can be verified by the presence of the implemented UI/JS changes or a PR that implements them. When you have PRs merging these changes, post the PR URLs here and I will verify and mark items done.

Label: enhancement

Related Preconditioning PR: https://github.com/EchoPath-Source/EchoPath-Preconditioning-Lab/pull/124
