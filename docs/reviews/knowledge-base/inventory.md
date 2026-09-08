<!-- Copyright The Linux Foundation and each contributor to LFX. -->
<!-- SPDX-License-Identifier: MIT -->

# Inventory

Empirical patterns where a change shipped a new skill, agent, or
contributor-facing file and the human-facing listings in `README.md` did not
move with it. Discovery is automatic; listings are not.

**Read when:** `README.md`, `CLAUDE.md`, or `AGENTS.md` changed, or the range
adds or removes a `skills/<name>/` directory or an `agents/*.md` file.

---

## `inventory/readme-must-list-new-surfaces` — Important

**Pattern:** a new `skills/<name>/` directory, `agents/<name>.md` file,
`CLAUDE.md`, or `AGENTS.md` is added, and `README.md` does not name it in
the project-structure tree, or (for a skill or agent) in the README table
that matches its kind.

**Detect:** for every new `skills/<name>/` directory, `agents/<name>.md`
file, `CLAUDE.md`, or `AGENTS.md` the range adds, confirm the
project-structure tree names it. A new skill must also appear in the skills
table; a new agent must also appear in the agents table. Do not require a
skill in the agents table, or an agent in the skills table. Root instruction
files (`CLAUDE.md`, `AGENTS.md`) need only the tree. Do not flag a
pre-existing omission the range did not introduce.

**Empirical citation:** PR #71 `CLAUDE.md` — Copilot — "the `README.md`
Project Structure tree lists root-level files but omits both new instruction
surfaces, `CLAUDE.md` and `AGENTS.md`." Resolved in `bb367cc`. Also PR #64
`README.md` — Copilot — "The central table now documents these two skill
directories, but the repository-layout tree later in this README still omits
both." Also PR #59 `README.md` — dealako — "This header says Reviewer agents
(8) and the table below lists 8, but `agents/` ships 13 files."

**Failure message:** a newly shipped skill, agent, or root instruction file
is missing from the README listing that covers it.

**Fix:** add the new path to the project-structure tree, and to the matching
README table when the path is a skill or agent, in the same change. Update
the count in the section heading if it states one.
