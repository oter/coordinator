## Summary

<!-- What does this change do, and why? -->

## Specification

<!-- The section of docs/spec.md that this change implements or changes. -->

## Checks

- [ ] `cd mcp && test -z "$(gofmt -l .)" && go vet ./... && go test -race ./...`
- [ ] `cd channels/slack && test -z "$(gofmt -l .)" && go vet ./... && go test -race ./...`
- [ ] `sh tests/test.sh`
- [ ] `node --test agents/agents_test.mjs`
- [ ] shellcheck on every `*.sh` file
- [ ] `npx -y markdownlint-cli2 '**/*.md' '#node_modules'`
- [ ] `claude plugin validate .`
- [ ] The documentation and the code change are in this pull request.
- [ ] The documentation uses ASD-STE100 Simplified Technical English.

## Test counts

<!-- Tests that ran, passed, failed, and were skipped. A skipped test in a required suite is a finding. -->
