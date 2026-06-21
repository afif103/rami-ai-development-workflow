Rami Afif AI Development Workflow
Version 2.6 — Consolidated Full Edition
Author: Rami Afif

======================================================================
DOCUMENT STATUS
======================================================================

This document is the complete consolidated AI Development Workflow
Version 2.6 approved by Rami Afif.

Version 2.6 keeps the rules and structure of Version 2.5 and adds the
Iterative Revised-Plan Re-Challenge Loop.

This workflow applies to serious software-development projects unless
Rami explicitly approves a different process for a specific project.

The workflow is designed to produce careful, reviewable, evidence-based
changes while keeping the human owner in control of every irreversible
or repository-changing action.

======================================================================
1. PURPOSE
======================================================================

The workflow exists to prevent common AI-assisted development failures:

- implementing from assumptions instead of repository evidence;
- allowing one AI to plan and approve its own work without challenge;
- making changes before architecture and boundaries are understood;
- mixing multiple implementers in one project;
- changing too many things in one packet;
- hiding uncertainty behind confident language;
- claiming success without executable verification;
- modifying unrelated or protected files;
- committing or pushing changes before human review;
- silently changing scope during implementation;
- accepting a green test suite that does not prove the requirement;
- losing project state between chats;
- repeating the same mistake in later packets;
- replacing a challenged plan with a new plan that was never challenged.

The workflow combines:

- one accountable architect and approval gate;
- one repository-grounded implementer per project;
- formal technical challenge before implementation;
- iterative re-challenge when the plan materially changes;
- small development packets;
- requirement-to-test traceability;
- executable quality gates;
- actual diff review;
- human approval before each repository-changing stage;
- a controlled learning loop after every completed packet.

======================================================================
2. CORE ROLES
======================================================================

2.1 Human Owner — Rami Afif

Rami is the final decision-maker and authorization authority.

Only Rami may approve:

- the packet direction;
- implementation;
- staging and commit;
- push;
- pull-request creation;
- merge;
- local synchronization after merge;
- feature-branch cleanup;
- deployment;
- destructive repository actions;
- changes to protected files;
- changes to this workflow.

Silence, lack of objection, or a previous approval does not count as
approval for a later gate.

Each approval is limited to the action and packet explicitly named.

2.2 ChatGPT GPT-5.5 Thinking — Architect and Independent Gate

ChatGPT GPT-5.5 Thinking is the:

- architect;
- requirements analyst;
- packet planner;
- risk analyst;
- acceptance-criteria author;
- independent reviewer;
- quality gate;
- final recommendation source before human decisions.

ChatGPT must:

- understand the business and user objective;
- use the supplied repository evidence and project history;
- define a narrow packet;
- state what is in scope and out of scope;
- identify architectural risks;
- prepare repository-grounded challenge prompts;
- independently review Claude Code’s challenge response;
- resolve or escalate material disagreements;
- review implementation reports and actual diffs;
- verify requirement-to-test traceability;
- decide whether a packet is ready for the next human approval;
- never treat its own plan as automatically correct.

ChatGPT must not act as the code implementer for a project assigned to
Claude Code.

2.3 Claude Code — Primary Implementer and Technical Challenger

Claude Code is the primary implementer for serious projects assigned to
Claude.

Before implementation, Claude must act as a repository-grounded
technical challenger.

Claude must:

- inspect the actual repository;
- test the architect’s assumptions against code and tests;
- identify architecture conflicts;
- identify hidden dependencies;
- identify unsafe boundaries;
- identify missing tests;
- challenge overbroad or untestable acceptance criteria;
- return one formal Challenge Protocol status;
- stop before implementation until human authorization is given;
- implement only the approved packet;
- report exact file impact and verification results;
- avoid unrelated changes;
- stop at each approval gate.

2.4 Codex CLI — Backup Implementer for Separate Projects

Codex CLI may be used as a second or backup implementer only for
separate projects, practice projects, or experimental projects assigned
to Codex.

Codex must not be introduced into a project already assigned to Claude
Code merely because Claude usage limits were reached.

The one-implementer rule applies to Codex in the same way it applies to
Claude.

2.5 Read-Only Specialist Reviewers

Additional AI models or specialist reviewers may be used for:

- security review;
- performance review;
- test review;
- architecture review;
- UI review;
- documentation review;
- domain review.

Unless explicitly authorized otherwise, specialist reviewers are
read-only.

They may inspect and advise but must not edit, stage, commit, push,
merge, deploy, clean, reset, restore, or discard repository work.

======================================================================
3. ONE IMPLEMENTER PER PROJECT
======================================================================

Each serious project must have one primary implementer.

For a Claude-assigned project:

- Claude Code performs implementation.
- ChatGPT plans and reviews.
- Codex does not implement in that same project.

For a Codex-assigned project:

- Codex performs implementation.
- ChatGPT plans and reviews.
- Claude does not implement in that same project.

A project may change implementers only through an explicit human
decision and a controlled handoff.

A controlled implementer handoff must include:

- current repository state;
- current branch and commit;
- working-tree condition;
- protected files;
- completed packets;
- unfinished packet status;
- approved architecture;
- unresolved risks;
- test status;
- explicit human approval for the transfer.

The one-implementer rule prevents:

- conflicting coding styles;
- duplicated or competing changes;
- unclear accountability;
- one model repairing another model’s unreviewed work;
- hidden context loss;
- difficult root-cause analysis.

======================================================================
4. DEVELOPMENT PACKETS
======================================================================

Serious development work must be divided into small, reviewable packets.

A packet should have:

- one primary objective;
- a clearly stated user or system value;
- limited architectural responsibility;
- defined file boundaries where reasonably predictable;
- explicit acceptance criteria;
- explicit verification;
- explicit out-of-scope items;
- a clear stop condition.

A packet must not become a container for unrelated cleanup.

If implementation reveals a separate issue, that issue should normally
be documented and deferred to a new packet.

A packet may be split when:

- architecture and behavior changes are too tightly mixed;
- the diff is becoming difficult to review;
- one foundation must exist before safe behavior changes are possible;
- independent verification is easier in smaller stages;
- rollback risk would be reduced;
- the implementer identifies hidden dependencies;
- the challenge protocol proves that the original packet is too broad.

Directional roadmap items are not implementation authorization.

Only the specific packet approved by Rami may proceed.

======================================================================
5. PACKET DESIGN BY CHATGPT
======================================================================

Before Claude inspects the repository, ChatGPT prepares the provisional
packet architecture.

The packet design should contain:

- packet name and identifier;
- current-state assessment;
- user value;
- problem statement;
- intended architectural result;
- repository checkpoint if known;
- required invariants;
- risks;
- proposed boundaries;
- provisional file impact;
- acceptance criteria;
- automated verification;
- required manual tests;
- privacy and safety constraints;
- explicit out-of-scope items;
- protected-file rules;
- stop conditions;
- approval boundaries.

ChatGPT must clearly distinguish:

- known repository facts;
- facts supplied by the user;
- architectural assumptions;
- unresolved questions.

ChatGPT must not represent assumptions as confirmed facts.

======================================================================
6. ARCHITECT–IMPLEMENTER CHALLENGE PROTOCOL
======================================================================

6.1 Purpose

Before implementation, Claude Code must inspect the actual repository
and challenge the packet.

The purpose is not to obtain automatic agreement.

The purpose is to test whether the architect’s plan survives contact
with the real codebase.

6.2 Read-Only Boundary

The initial Challenge Protocol is read-only.

Unless separately authorized, Claude must not:

- edit files;
- create files;
- create a branch;
- apply a patch;
- run an editing agent;
- install or upgrade dependencies;
- run formatters or autofixers;
- stage;
- commit;
- push;
- create a pull request;
- merge;
- reset;
- restore;
- clean;
- stash;
- delete;
- rename;
- move;
- overwrite;
- discard work.

Read-only test execution may also be prohibited when it could create
caches, generated files, snapshots, databases, or other changes.

6.3 Required Status

Claude must return exactly one formal status:

ACCEPT
- The proposed packet is repository-compatible and ready to become an
  implementation prompt.
- No material architectural issue remains.

ACCEPT WITH MINOR NOTES
- The direction is correct.
- Only small clarifications or non-material adjustments are needed.
- The notes must not change architecture, safety, scope, core files, or
  acceptance behavior.

CHALLENGE
- The packet is feasible, but one or more material assumptions,
  boundaries, acceptance criteria, dependencies, tests, or design
  choices must be revised before implementation.

BLOCK
- Implementation should not proceed because of a checkpoint mismatch,
  missing prerequisite, unsafe repository condition, incompatible
  architecture, unresolvable ambiguity, or another blocking issue.

6.4 Expected Challenge Content

The challenge report should normally include:

- checkpoint verification;
- repository-grounded pipeline or architecture map;
- confirmed facts;
- unsupported assumptions;
- hidden dependencies;
- challenge severity;
- minimum safe design;
- expected file impact;
- expected test impact;
- packet-boundary review;
- acceptance-criteria review;
- implementation-readiness decision.

Claude must stop after the report.

Claude must not treat ACCEPT as implementation authorization.

======================================================================
7. ITERATIVE REVISED-PLAN RE-CHALLENGE LOOP — VERSION 2.6
======================================================================

7.1 Core Rule

The Challenge Protocol is not limited to one challenge or one
re-challenge.

After any Claude status of CHALLENGE or BLOCK, ChatGPT reviews the
report.

If ChatGPT materially revises the plan, the revised plan must be sent
back to Claude for another repository-grounded challenge before any
implementation approval.

This may continue to:

- a second challenge;
- a third challenge;
- a fourth challenge;
- or as many rounds as are required.

The loop ends only when no unresolved material issue remains.

7.2 Material Changes That Require Another Challenge

Another challenge is required when ChatGPT changes any of the
following materially:

- system architecture;
- packet objective;
- packet split;
- technical boundary;
- state ownership;
- data contract;
- thread or process responsibility;
- lifecycle behavior;
- privacy or safety behavior;
- file impact;
- dependency impact;
- test strategy;
- manual-test plan;
- acceptance criteria;
- rollback behavior;
- compatibility strategy;
- implementation sequence;
- an out-of-scope item into an in-scope item;
- an in-scope item into an out-of-scope item;
- any design that Claude has not yet repository-checked.

7.3 Changes That Normally Do Not Require Another Challenge

Another challenge is normally not required when ChatGPT only:

- accepts Claude’s already-reviewed recommendation;
- chooses between alternatives that Claude already examined and found
  safe;
- makes wording corrections;
- improves formatting;
- adds explanation without changing behavior;
- clarifies a requirement already present;
- removes ambiguity without changing architecture, scope, safety,
  files, tests, or acceptance behavior.

7.4 Challenge Status in Every Round

Every challenge round must still return exactly one status:

- ACCEPT;
- ACCEPT WITH MINOR NOTES;
- CHALLENGE;
- BLOCK.

A later round does not become informal simply because earlier rounds
already occurred.

7.5 Human Control

The loop does not authorize implementation.

Implementation may begin only when:

1. there is no unresolved material CHALLENGE or BLOCK;
2. ChatGPT has independently reviewed the latest report;
3. the final implementation prompt does not materially depart from the
   latest challenged and resolved design;
4. Rami explicitly authorizes implementation.

7.6 Implementation Prompt Re-Challenge

If the final implementation prompt introduces a material design,
scope, file, test, or acceptance change that was not present in the
latest challenged plan, the prompt itself must go through another
Challenge Protocol round before implementation.

7.7 Purpose of the Iterative Loop

This rule prevents ChatGPT from:

- rejecting Claude’s design;
- inventing a materially new replacement;
- declaring the new replacement ready;
- and authorizing implementation without repository challenge.

The architect and implementer must continue challenging each other
until the final plan is repository-grounded and all material issues are
resolved.

======================================================================
7A. POST-IMPLEMENTATION REVIEWER–IMPLEMENTER CHALLENGE GATE
======================================================================

7A.1 Purpose

After implementation, ChatGPT must independently review the implementation
report and the actual diff or approved review artifact.

When ChatGPT identifies a material post-implementation issue and proposes a
correction, Claude Code must first perform a focused, read-only,
repository-grounded technical challenge of that finding before any correction
edits are authorized.

This prevents ChatGPT from unilaterally directing a technically risky
correction without allowing the repository implementer to verify the finding
and proposed fix.

7A.2 When This Gate Is Required

Use this gate for material findings involving:

- concurrency or race conditions;
- architecture or data contracts;
- data loss, corruption, or stale-state risks;
- security or privacy;
- lifecycle, ownership, isolation, or stale-worker behavior;
- backward compatibility;
- destructive behavior;
- major test-strategy changes;
- corrections that could introduce another significant technical risk.

7A.3 When This Gate Is Normally Not Required

A focused challenge is normally unnecessary for non-material corrections such
as:

- typos;
- comments or wording;
- formatting;
- obvious test-name corrections;
- small documentation errors;
- clearly mechanical fixes with no architectural, behavioral, safety,
  compatibility, privacy, or data-risk impact.

7A.4 Required Process

1. Claude implements only after explicit human authorization.
2. Claude returns the implementation report and complete diff-review material.
3. ChatGPT independently reviews the actual implementation evidence.
4. If ChatGPT finds a material issue, the packet is placed on HOLD and no
   correction is authorized yet.
5. Claude performs a focused read-only technical challenge of:
   - the reported issue;
   - ChatGPT's reasoning;
   - the proposed correction;
   - any additional risks.
6. Claude returns exactly one formal status:
   - ACCEPT;
   - ACCEPT WITH MINOR NOTES;
   - CHALLENGE;
   - BLOCK.
7. ChatGPT independently reviews Claude's focused challenge.
8. If ChatGPT materially revises the correction design, the Version 2.6
   Iterative Re-Challenge Loop applies again, including third, fourth, or later
   challenges as needed.
9. Rami explicitly authorizes the correction before Claude edits.
10. Claude performs only the approved correction, reruns required
    verification, and returns updated diff evidence.
11. ChatGPT reviews the corrected actual diff before any staging or commit
    approval.

7A.5 Authorization and Safety

The focused post-implementation challenge is read-only unless Rami separately
authorizes correction implementation.

During the challenge, Claude must not:

- edit;
- stage;
- commit;
- push;
- create a pull request;
- merge;
- synchronize;
- clean;
- reset;
- restore;
- stash;
- delete;
- modify protected files.

A passing test suite does not override a material independent-review finding.

This gate applies to all serious projects using this workflow.

======================================================================
7B. IMPLEMENTATION VISIBILITY AND TRANSPARENCY RULE
======================================================================

7B.1 Core Principle

Claude Code may use scripts, patch tools, write tools, or other editing methods
without displaying every changed line live.

Quiet editing is allowed, but invisible completion is not.

The human and ChatGPT must always receive enough evidence to understand:

- what Claude intended to change;
- what Claude actually changed;
- which files were touched;
- whether protected files remained safe;
- whether verification passed.

Human-facing principle:

"Claude may edit quietly, but it must never finish invisibly."

7B.2 Before Editing

Before editing, Claude must state:

- the packet being implemented;
- the exact files it expects to edit or create;
- the purpose of each expected file change;
- protected files or areas that must remain untouched.

If Claude later discovers that another file must change, it must stop and obtain
approval or return a challenge when the added file materially expands scope.

7B.3 During Longer Implementation

Claude should provide brief progress updates at meaningful milestones, such as:

- production structure added;
- compatibility path preserved;
- focused tests added;
- verification started;
- material issue discovered.

Claude does not need to print every code line or every low-level command.

Progress updates must be concise and must not replace final evidence.

7B.4 After Editing

Claude must provide:

- exact changed-file list;
- `git status --short` or equivalent repository status;
- diff statistics;
- complete diff evidence or an approved external review artifact;
- exact verification commands and results;
- confirmation that protected files were not modified;
- confirmation that nothing was staged or committed unless separately
  authorized.

7B.5 Small Versus Large Changes

For a tiny, localized change, Claude should normally show the exact patch
directly when practical.

For a larger packet, a complete external diff artifact is preferred over
flooding the screen with hundreds of lines.

The review artifact must include untracked new files, not only tracked
`git diff` output.

7B.6 Independent Review Requirement

ChatGPT must review the actual diff or approved review artifact, not only
Claude's summary, before recommending staging or commit.

A packet may not proceed to commit merely because Claude reports that tests
passed.

If the diff changes after review, the changed diff must be reviewed again.

7B.7 Future CLAUDE.md Alignment

After the current active packet is safely completed and closed, prepare a
separate controlled workflow-maintenance task to align the project's protected
`CLAUDE.md` with the applicable Version 2.6 rules.

That future update should include concise repository instructions for:

- the iterative re-challenge loop;
- the post-implementation reviewer–implementer challenge gate;
- implementation visibility and transparency;
- separate human approval gates.

Do not mix a protected `CLAUDE.md` update into an unrelated feature packet.

======================================================================
8. HUMAN APPROVAL GATES
======================================================================

Each major action requires a separate approval.

Approval for one stage does not include later stages.

8.1 Architecture Approval

Rami approves the packet direction and finalized architecture.

This does not authorize implementation.

8.2 Implementation-Prompt Approval

Rami approves the exact Claude Code implementation prompt.

This does not necessarily authorize implementation unless the approval
explicitly says so.

8.3 Implementation Approval

Rami explicitly authorizes Claude to edit and test the named packet.

This approval does not authorize:

- staging;
- commit;
- push;
- pull request;
- merge;
- deployment;
- synchronization;
- cleanup.

8.4 Staging and Commit Approval

After implementation and diff review, Rami separately authorizes:

- staging the approved files;
- creating one specific commit.

The commit scope and subject should be stated before execution.

8.5 Push Approval

A committed change must not be pushed until Rami separately approves
the push.

8.6 Pull-Request Approval

A pull request must not be created until Rami separately approves it.

The PR title, body, branch, base branch, and evidence should be
reviewable before creation where practical.

8.7 Merge Approval

A pull request must not be merged until:

- CI is complete;
- review findings are resolved;
- the final diff is accepted;
- Rami explicitly authorizes merge.

8.8 Local Synchronization Approval

After remote merge, the local repository must not be synchronized
automatically.

Fetching, checking out the target branch, pulling, or fast-forwarding
local state requires separate approval.

8.9 Branch Cleanup Approval

Deleting local or remote feature branches requires separate approval.

8.10 Deployment Approval

Deployment is always a separate approval unless Rami explicitly
combines it with another named action.

8.11 Destructive Action Approval

The following always require explicit approval:

- reset;
- restore;
- clean;
- stash;
- deleting untracked files;
- overwriting local work;
- force push;
- branch deletion;
- database destruction;
- migration rollback;
- secret rotation;
- production changes.

======================================================================
9. REPOSITORY CHECKPOINT AND SAFETY
======================================================================

Before a challenge or implementation packet, record where applicable:

- repository name;
- local path;
- expected current branch;
- expected local HEAD;
- expected remote-tracking HEAD;
- working-tree condition;
- staged changes;
- untracked files;
- protected files;
- approved review artifacts;
- relevant commit and PR history.

If the actual checkpoint differs materially from the expected
checkpoint, Claude should normally return BLOCK and stop.

Protected files must be listed explicitly.

Protected files must not be:

- edited;
- staged;
- committed;
- deleted;
- cleaned;
- overwritten;
- renamed;
- moved;
- restored from another location;

unless separately authorized.

Files intentionally stored outside the repository must not be searched
for, restored, copied, or added merely because they existed in the
past.

======================================================================
10. IMPLEMENTATION RULES
======================================================================

Once implementation is explicitly authorized, Claude must:

- implement only the named packet;
- respect the approved architecture;
- stay within the approved boundaries;
- preserve protected files;
- avoid unrelated refactors;
- avoid opportunistic cleanup;
- keep changes reviewable;
- maintain backward compatibility where required;
- add or update tests required by the acceptance criteria;
- report deviations immediately;
- stop when a material new issue requires architecture review.

Claude must not silently redesign the packet while coding.

If implementation reveals a material architecture conflict, Claude
must stop and return a challenge rather than improvise a new design.

Implementation authorization does not include staging or commit.

======================================================================
11. REQUIREMENT-TO-TEST TRACEABILITY
======================================================================

Every material requirement must be connected to evidence.

The packet should maintain traceability between:

- requirement;
- code path;
- automated test;
- manual test where required;
- verification result.

A useful traceability record includes:

- requirement identifier;
- expected behavior;
- responsible file or component;
- test name;
- test type;
- result;
- remaining limitation.

A green suite is not enough when the changed requirement is not
directly tested.

Tests should prove:

- the new behavior;
- relevant failure behavior;
- preserved old behavior;
- boundary conditions;
- ownership and isolation;
- compatibility;
- error handling;
- security or privacy constraints;
- regression-sensitive paths.

Tests must not be created merely to mirror the implementation without
testing user-visible or architectural requirements.

======================================================================
12. EXECUTABLE QUALITY GATES
======================================================================

Each packet must define appropriate executable gates.

Depending on the repository, these may include:

- syntax or compilation checks;
- type checks;
- lint checks;
- formatter checks;
- focused unit tests;
- focused integration tests;
- regression tests;
- full test suite;
- headless suite;
- UI smoke tests;
- database migration tests;
- build;
- packaging checks;
- security checks;
- performance benchmarks;
- CI.

Verification commands and results must be reported exactly.

Claude must not claim that a command passed if it was not run.

Skipped tests, warnings, environmental limits, flaky tests, and
expected count differences must be reported.

A failing unrelated test must be investigated enough to establish
whether it is:

- introduced by the packet;
- pre-existing;
- environmental;
- genuinely unrelated;
- blocking.

======================================================================
13. MANUAL TESTING
======================================================================

Automated tests do not replace necessary manual validation.

Packets involving the following normally require manual tests:

- microphones;
- audio devices;
- system audio;
- live timing;
- UI state;
- installers;
- operating-system integration;
- external services;
- human interaction flow;
- real latency;
- visual behavior;
- hardware.

Manual tests should specify:

- setup;
- exact actions;
- expected result;
- failure signs;
- privacy constraints;
- evidence captured;
- whether the test passed.

Manual testing must not be described as passed unless it was actually
performed.

======================================================================
14. DIFF REVIEW PACKAGE
======================================================================

After implementation and verification, Claude must prepare a diff
review package before staging or commit.

The package should include:

- repository checkpoint;
- branch;
- changed-file list;
- diff statistics;
- complete diff or approved review artifact;
- requirement-to-test mapping;
- test commands and results;
- manual-test status;
- known limitations;
- deferred issues;
- protected-file confirmation;
- working-tree status;
- explicit statement that staging and commit have not occurred.

For large diffs, a review artifact may be created outside the
repository when authorized.

The artifact should record:

- filename;
- absolute location;
- SHA-256;
- byte size;
- line count;
- changed-file count.

The reviewed artifact must match the intended commit.

If the diff changes after approval, it must be reviewed again.

======================================================================
15. INDEPENDENT REVIEW
======================================================================

ChatGPT must independently review the actual change.

The review should evaluate:

- correctness;
- scope compliance;
- architecture compliance;
- acceptance criteria;
- test coverage;
- compatibility;
- privacy;
- security;
- concurrency;
- state ownership;
- stale-worker behavior;
- error paths;
- dead code;
- hidden behavior changes;
- unnecessary complexity;
- documentation accuracy;
- protected-file safety.

ChatGPT must not rely only on Claude’s summary.

The actual diff, report, or review artifact must be examined.

Review findings should be classified by severity where useful:

- blocking;
- major;
- minor;
- informational.

A packet is not ready for commit merely because implementation tests
passed.

======================================================================
16. PACKET REPORT CARD
======================================================================

Before the commit gate, the packet should receive a report card.

The report card may include:

- Objective achieved: PASS / FAIL / PARTIAL
- Scope control: PASS / FAIL
- Architecture compliance: PASS / FAIL
- Challenge resolution: PASS / FAIL
- Requirement traceability: PASS / FAIL
- Focused tests: PASS / FAIL
- Full regression: PASS / FAIL
- Manual tests: PASS / FAIL / NOT YET RUN
- Privacy and safety: PASS / FAIL
- Protected files: PASS / FAIL
- Diff review: PASS / FAIL
- Remaining risks: NONE / LISTED
- Commit readiness: APPROVE / HOLD / REJECT

The report card is evidence for Rami’s decision.

It is not an automatic authorization.

======================================================================
17. STAGING AND COMMIT
======================================================================

After Rami approves staging and commit:

- stage only the reviewed files;
- verify the staged file list;
- verify the staged diff;
- confirm protected files are absent;
- create the approved commit;
- use the approved subject;
- avoid unapproved trailers;
- report the resulting commit hash;
- verify working-tree status.

If the staged diff differs from the reviewed diff, stop before commit.

One packet should normally produce one focused commit unless a
different structure is explicitly approved.

======================================================================
18. PUSH, PULL REQUEST, AND MERGE
======================================================================

18.1 Push

After separate push approval:

- verify branch and commit;
- push the intended branch only;
- report the remote result;
- do not create a PR unless separately approved.

18.2 Pull Request

After separate PR approval:

- use the approved base and head;
- include packet objective;
- summarize architecture;
- include tests;
- include manual-test evidence;
- list limitations;
- avoid claiming unperformed checks;
- report the PR number and URL or identifier.

18.3 CI and Review

Before merge:

- wait for CI to complete;
- inspect failures;
- verify the final PR diff;
- confirm no new commits appeared unexpectedly;
- resolve review findings;
- update the report card.

18.4 Merge

After explicit merge approval:

- use the approved merge method;
- report the merge commit;
- report its parentage where relevant;
- verify the target remote branch;
- do not synchronize local state automatically.

======================================================================
19. LOCAL SYNCHRONIZATION AND BRANCH CLEANUP
======================================================================

After merge, local synchronization is a separate controlled stage.

With approval, verify:

- current local branch;
- working tree;
- remote target commit;
- intended synchronization method.

After synchronization, report:

- local target branch commit;
- remote target commit;
- whether they match;
- working-tree condition.

Feature-branch cleanup requires another approval.

Before deleting a branch, verify:

- PR is merged;
- target branch contains the feature commit;
- no uncommitted work exists;
- no unpushed work exists;
- correct local and remote branch names are known.

Local and remote deletion must be reported separately.

======================================================================
20. CONTROLLED WORKFLOW LEARNING LOOP
======================================================================

After every completed packet, perform a Controlled Workflow Learning
Loop.

The purpose is to improve the workflow based on evidence without
allowing uncontrolled process changes.

20.1 Review What Happened

Record:

- what went well;
- what went wrong;
- what nearly went wrong;
- what took unnecessary time;
- what assumption failed;
- what review caught;
- what testing missed;
- what the human had to correct.

20.2 Determine Why

Identify the root cause.

Possible causes include:

- unclear requirement;
- wrong architectural assumption;
- insufficient repository inspection;
- implementer mistake;
- reviewer mistake;
- missing test;
- weak acceptance criterion;
- packet too broad;
- hidden dependency;
- poor handoff;
- environmental issue;
- tool limitation;
- concurrency issue;
- privacy or safety issue;
- workflow gap.

20.3 Classify the Lesson

Classify the issue as one or more of:

- one-time mistake;
- repeated implementation mistake;
- repeated planning mistake;
- repeated review mistake;
- missing test;
- missing quality gate;
- missing challenge question;
- packet-sizing issue;
- safety-critical issue;
- privacy-critical issue;
- project-specific lesson;
- workflow-wide lesson.

20.4 Choose a Controlled Response

Possible responses include:

- no workflow change;
- add a project note;
- add a test;
- revise an acceptance-criteria template;
- add a challenge question;
- split future packets differently;
- update a repository instruction file;
- add a protected-file rule;
- add a quality gate;
- propose a workflow version change.

20.5 Human Approval for Workflow Changes

The workflow must not rewrite itself automatically.

Material workflow changes require Rami’s approval.

Project-specific lessons should not automatically become universal
rules unless there is evidence that they apply broadly.

20.6 Record the Outcome

At packet closure, record:

- lesson;
- classification;
- chosen action;
- whether the workflow changed;
- new version if applicable;
- deferred improvement.

======================================================================
21. HANDOFF AND CONTINUITY
======================================================================

When moving to a new chat or work session, provide a complete handoff.

A handoff should include:

- project and repository;
- local path;
- approved workflow version;
- current branch;
- local and remote commits;
- working-tree status;
- protected files;
- completed packets;
- current packet;
- challenge status;
- approved architecture;
- implementation status;
- test status;
- review artifact;
- commit, PR, and merge details;
- unresolved issues;
- next authorized action;
- actions explicitly not authorized.

A handoff is informational.

It does not authorize implementation or repository actions.

======================================================================
22. HONESTY AND EVIDENCE
======================================================================

All AI participants must distinguish:

- observed fact;
- user-provided fact;
- inference;
- proposal;
- unverified assumption.

Do not claim:

- a test passed when it was not run;
- a branch is clean when it was not checked;
- remote state is current when no fetch or remote verification occurred;
- a file is unchanged without evidence;
- behavior is preserved without tests or repository reasoning;
- a challenge is resolved when material disagreement remains.

When evidence is incomplete, state the limitation.

Confident wording must not replace proof.

======================================================================
23. PRIVACY, SECURITY, AND LOCAL-FIRST RULES
======================================================================

Project privacy and security boundaries must be treated as architecture,
not optional polish.

Packets must define where relevant:

- what data is stored;
- what data is logged;
- what leaves the device;
- what is sent to third parties;
- what is redacted;
- what is enabled by default;
- how secrets are handled;
- how stale data is cleared;
- how context is isolated.

Local-first projects must not introduce cloud processing, telemetry, or
external data transfer without explicit architecture review and human
approval.

Full private content should not be logged by default.

Security-sensitive changes require stronger testing and review.

======================================================================
24. PROHIBITED SHORTCUTS
======================================================================

The following shortcuts are prohibited unless explicitly approved:

- “Just implement it and we will review later.”
- “Commit everything.”
- “Clean the repository.”
- “Reset to make the tests pass.”
- “Use both Claude and Codex on the same project.”
- “Merge because CI is green.”
- “Push while waiting for review.”
- “Fix unrelated issues while here.”
- “Change the contract and update callers later.”
- “Treat the roadmap as implementation permission.”
- “Assume the architect’s revised plan is correct without re-challenge.”
- “Skip manual hardware or UI tests because unit tests passed.”
- “Delete untracked files because they are not committed.”
- “Use the longest or most coherent output as truth without evidence.”
- “Hide failed or skipped verification.”
- “Continue after discovering a material architecture conflict.”

======================================================================
25. APPROVAL LANGUAGE
======================================================================

Approvals should be explicit and narrow.

Examples:

Architecture:
“I approve the finalized architecture for Packet X. Prepare the
implementation prompt, but do not authorize implementation yet.”

Implementation:
“I authorize Claude Code to implement Packet X only. Do not stage,
commit, push, create a PR, merge, synchronize, or clean up.”

Commit:
“I approve staging the reviewed files and creating the approved commit
for Packet X. Do not push.”

Push:
“I approve pushing the Packet X feature branch. Do not create a PR.”

Pull request:
“I approve creation of the Packet X pull request. Do not merge.”

Merge:
“I approve merging PR #X using the approved merge method. Do not
synchronize local state yet.”

Synchronization:
“I approve synchronizing local main with the merged remote main. Do not
delete branches.”

Cleanup:
“I approve deleting the confirmed merged local and remote feature
branches.”

Broad statements such as “go ahead,” “continue,” or “do everything”
should not be interpreted beyond the immediate clearly established
stage.

======================================================================
26. STANDARD PACKET LIFECYCLE
======================================================================

A normal serious packet follows this order:

1. Project state and handoff verified.
2. ChatGPT assesses current state and recommends a packet.
3. Rami approves the packet direction when required.
4. ChatGPT prepares the read-only Challenge Protocol prompt.
5. Claude inspects the repository.
6. Claude returns ACCEPT, ACCEPT WITH MINOR NOTES, CHALLENGE, or BLOCK.
7. ChatGPT independently reviews the report.
8. If the plan materially changes, run another challenge.
9. Repeat the challenge loop until no material issue remains.
10. Rami approves the finalized architecture.
11. ChatGPT prepares the exact implementation prompt.
12. Confirm the prompt introduces no unchallenged material change.
13. Rami explicitly authorizes implementation.
14. Claude states the expected file impact, implements, provides milestone
    visibility, and runs the approved verification.
15. Claude prepares the implementation report and complete diff review package.
16. ChatGPT independently reviews the actual diff and evidence.
17. If ChatGPT finds a material issue, Claude performs the focused
    Post-Implementation Reviewer–Implementer Challenge before any correction.
18. Rami explicitly authorizes any material correction.
19. Claude performs only the approved correction and returns updated evidence.
20. ChatGPT reviews the corrected actual diff.
21. Required manual tests are performed.
19. ChatGPT produces a packet report card.
20. Rami approves or rejects staging and commit.
21. If approved, Claude stages and commits only the reviewed change.
22. Rami separately approves or rejects push.
23. Rami separately approves or rejects PR creation.
24. CI and final PR review complete.
25. Rami separately approves or rejects merge.
26. Rami separately approves or rejects local synchronization.
27. Rami separately approves or rejects branch cleanup.
28. Controlled Workflow Learning Loop is completed.
29. Packet is marked shipped and closed.
30. Project registry and handoff are updated.

======================================================================
27. VERSION 2.6 CHANGE FROM VERSION 2.5
======================================================================

Version 2.5 introduced the formal Architect–Implementer Challenge
Protocol before implementation.

Version 2.6 strengthens that rule with three related controls:

1. The Iterative Revised-Plan Re-Challenge Loop.
2. The Post-Implementation Reviewer–Implementer Challenge Gate.
3. The Implementation Visibility and Transparency Rule.

A revised plan is not automatically approved merely because ChatGPT created it
in response to Claude's challenge. When the revision is material, Claude must
inspect and challenge it again. The process can repeat for a third, fourth, or
later challenge until all material concerns are resolved.

After implementation, a material issue found by ChatGPT is not automatically
sent back as an editing instruction. Claude first performs a focused read-only
technical challenge of the finding and proposed correction. Rami then
explicitly authorizes the correction.

Claude may use efficient editing tools without displaying every changed line
live, but it must announce intended file impact, provide milestone visibility
during longer work, and finish with complete diff and verification evidence.

No new version number is required for each challenge round or for these
approved refinements. They remain part of Version 2.6.

======================================================================
28. FINAL GOVERNANCE RULE
======================================================================

No AI participant may authorize itself.

ChatGPT cannot authorize implementation.

Claude cannot authorize implementation.

Codex cannot authorize implementation.

CI cannot authorize merge.

A passing test suite cannot authorize commit.

A roadmap cannot authorize work.

Only Rami may approve the next controlled action.

======================================================================
END OF AI DEVELOPMENT WORKFLOW VERSION 2.6
======================================================================

