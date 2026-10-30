# Executable work template

Use for a bounded implementation, artifact, integration or separately assigned verification result. Link the feature brief instead of repeating its history.

Replace braces with actual context and remove unused prompts. Keep unanswered consequential questions explicit. This is a writing aid, not a server schema or an authorization.

```markdown
# {Result to produce}

Contract: {current task/specification reference and revision; method and version if applicable}
Contribution: {canonical parent/outcome or none; this is not a prerequisite}
Mode: executable

## Objective and boundaries

{Concrete result and why needed. Included change, explicit exclusions and relevant established requirements.}

## Inputs and prerequisites

{Readable specifications, decisions, producer outputs and relevant code/design references with versions.}
{For each real prerequisite: producer reference + exact required output. State unmet requirements; no implicit sibling ordering.}

## Execution requirements

{Expertise and access the work needs, who may execute it (proposed availability), current constraints and applicable repository/project policy references.}
{Existing authorization for this scope; actions requiring separate approval, if any. Unknown authority stays unknown.}

## Observable acceptance

- {AC1: context, action and expected externally observable result}
- {Relevant error/recovery case}
- {Relevant authorized/unauthorized actor or cross-space case}

## Verification plan

{Check route/evidence for each criterion, required review/quality policy references and known limits. Implementation hints are optional and must be distinguished from accepted constraints.}

## Open decisions and interruption

{Question reference (a comment that mentions the person), affected action, the person asked if known, other blockers and safe next action. Omit when none.}

## Result and handoff

{Produced artifact/commit/revision, criterion-level observed checks/results, verifier and governing contract/policy version.}
{Review/acceptance and release disposition separately; outstanding blockers, latest artifact and concrete continuation step.}
```
