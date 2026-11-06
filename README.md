# TDD Agent Skills

Agent skills for a human-reviewed, test-verified AI development workflow.

## Skills
- `tdd-spec`: clarify expected behavior and write `{feature-title}-spec.md`.
- `tdd-tests`: derive implementation-independent test scenarios from the approved spec.
- `tdd-implement`: implement with tests as an adaptive feedback loop.
- `tdd-verify`: independently challenge the implementation against requirements and evidence.

## Suggested workflow
1. Run `tdd-spec`; review and approve the generated `{feature-title}-spec.md`.
2. Run `tdd-tests`; review and approve the test scenarios.
3. Run `tdd-implement`.
4. Run `tdd-verify`; address findings before human acceptance.

## Usage

```shell
$ npx skills add https://github.com/sivaprasadreddy/tdd-agent-skills
```
