# coordinator

coordinator is a Claude Code plugin. It holds the roles that coordinate Claude Code sessions across projects and machines:

- **bigm** (`coordinator:bigm`): the one session that the owner talks to. It keeps the ledger, starts the clankers, runs the sweep, and shows the owner only the questions that need the owner.
- **clanker** (`coordinator:clanker`): knows the full picture of one project. It divides the work into tasks and starts one clerk for each task.
- **clerk** (`coordinator:clerk`): owns one task. It runs a workflow, pushes, and reports with evidence.

The plugin also has:

- the MCP server in `mcp/` (Go, standard library only): mail, handoffs, questions and answers, reports, leases, role settings, sessions, monitors, and init;
- the hooks in `hooks/` and the scripts in `scripts/`: the handoff, the waiter, the refusal stop, the status line tap, and the board;
- the ledger template in `ledger-template/`: the private repository where bigm keeps the state of all work;
- the init skill `/coordinator:init`, which sets up the ledger, the projects, and the user settings;
- the Slack channel in `channels/slack/`.

The specification is [docs/spec.md](docs/spec.md).

## Install

```bash
claude plugin marketplace add oter/bruh
claude plugin install coordinator@oter
claude plugin install bruh@oter
```

The marketplace `oter` is in [oter/bruh](https://github.com/oter/bruh). `coordinator@oter` becomes installable when the `oter` marketplace lists it and bruh 0.13.0, which no longer has the roles, is released (steps 4 and 5 of the work plan of the plugin split). Until then, do not install it next to bruh 0.12.x: bruh 0.12.x still has its own copy of the roles, so each hook, the poller, and the board would run twice.

The coordinator needs the bruh plugin (`bruh@oter`): the clerks run its workflows (`/bruh:deliver`, `/bruh:tickets`, `/bruh:implement-tickets`, `/bruh:review-and-fix`, `/bruh:review-only`) and its skill `/bruh:implement`.

Then run `/coordinator:init` in a session with no role key, and start bigm in the ledger folder.

## Tests

```bash
go -C mcp test -race ./...
go -C channels/slack test -race ./...
node --test agents/agents_test.mjs
sh tests/test.sh
claude plugin validate .
```

## License

Apache-2.0. See [LICENSE](LICENSE). Report a vulnerability as [SECURITY.md](SECURITY.md) says.
