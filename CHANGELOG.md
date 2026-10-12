# Changelog

All notable changes to this project are recorded in this file.

## 0.13.0 [Unreleased]

Imported from oter/bruh at 7dc3fa0 (plus #58 from 6a39c0c), renamed to coordinator.

### Changed

- The plugin is `coordinator`, in the repository `oter/coordinator`, at version 0.13.0. Install it with `claude plugin install coordinator@oter`, and set its options with `/plugin configure coordinator`. Owner decision 2026-10-09 (Q-237, Q-238, Q-252).
- The plugin data folder is `~/.claude/plugins/data/coordinator-oter`. It follows from the plugin name. Upgrade note: the state in `~/.claude/plugins/data/bruh-oter` (the init config, mail, handoffs, questions, and holds) does not move by itself. The migration step that copies it to `coordinator-oter` is step 4 of the work plan of the plugin split. Do not switch before that step. Owner decision 2026-10-09 (Q-245, Q-251).
- The MCP server is `coordinator`, so the tool prefix is `mcp__plugin_coordinator_coordinator__`. The Slack tools have the prefix `mcp__plugin_coordinator_slack__`, and the Slack channel loads with `plugin:coordinator@oter`. Run `/coordinator:init` again, so that the user settings allow the new tool names. Agent-derived, needs owner decision.
- The agents are `coordinator:bigm`, `coordinator:clanker`, `coordinator:clerk`, and `coordinator:learner`. Owner decision 2026-10-09 (Q-237, Q-239).
- The init skill is `/coordinator:init`. Owner decision 2026-10-09 (Q-239).
- The workflows and the implement skill stay in the bruh plugin, and the roles call them by name: `/bruh:deliver`, `/bruh:tickets`, `/bruh:implement-tickets`, `/bruh:review-and-fix`, `/bruh:review-only`, and `/bruh:implement`. Owner decision 2026-10-09 (Q-239).
- The `Skill` hook of the bigm start settings passes `coordinator:` skills and `bruh:` skills. Agent-derived, needs owner decision.
