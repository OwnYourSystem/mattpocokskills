# Matt Pocock’s engineering skills in Codex Cloud

This repository vendors all 20 engineering skills and the seven productivity skills they reference under `.agents/skills/`. The snapshot includes each skill’s complete directory, with its `SKILL.md`, Codex metadata, references, and templates. The upstream license is included. [Pinned upstream commit](https://github.com/mattpocock/skills/tree/6f7f7831a625f040a8e06a0e7954826b87ce775a) · [MIT license](../.agents/skills/matt-pocock-LICENSE)

## Use in Codex Cloud

Start a fresh Codex Cloud task on a branch containing these files. Ask for a skill by name, for example, “Use the `tdd` skill.” In Codex clients with a skill picker, type `$` and choose the skill. When an upstream instruction calls for the “Skill tool,” Codex can use the named repository skill by reading its `SKILL.md`. [Codex skills documentation](https://developers.openai.com/codex/skills/)

Use `setup-matt-pocock-skills` when configuring this repository’s issue tracker, triage labels, or domain documents. It asks for choices and writes repository documentation. Remote tracker operations require a configured, authenticated GitHub or GitLab tool and the appropriate permissions. The upstream CLI examples use `gh` or `glab`. Workflows that delegate require subagent support in the current Codex session.

## Security and compatibility review

Codex discovery reads skill metadata from disk. Installation requires no package manager, plugin, hook, or script execution. Both bundled shell templates were reviewed and checked with `bash -n`.

- `diagnosing-bugs` includes an interactive Bash template that prints captured observations to the terminal. Its output should contain observations with sensitive values redacted.
- `wizard` includes an interactive Bash template that can open a browser, write to `.env`, and set GitHub repository secrets or variables through `gh`. Review a generated wizard’s file paths and destination repository before running it in a terminal. The template follows an existing `.env` symlink and retains existing file permissions.
- `improve-codebase-architecture` includes an HTML template that loads Tailwind and Mermaid JavaScript from external CDNs when opened. Use a local rendering path for reports containing sensitive repository material.
- Issue and PR workflows can write to remote trackers or push branches when invoked. Discovery was checked separately from those operations and from interactive template execution.

## Verify or update

In a fresh Codex session for the repository, check the skill picker for `tdd`, `setup-matt-pocock-skills`, and `grilling`. For a full check, query the Codex app server’s `skills/list` with the repository root in `cwds` and `forceReload` set to `true`. On Codex CLI 0.172.0-alpha.2, this check returned all 27 repository entries enabled and zero discovery errors for the installed paths. In this checkout, the app server reported names with the `mattpocock-skills:` prefix, for example `mattpocock-skills:tdd`.

To update, review a specific upstream revision, copy the complete engineering and referenced productivity directories, and keep the license and commit link current. Compare the copied trees against that revision, syntax-check each Bash template, and repeat the discovery check.
