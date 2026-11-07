# Agent skills

Personal standalone agent skills.

## Set up another computer

Install Git, authenticate with GitHub, and install Codex. Then clone this repo.

Windows (PowerShell):

```powershell
git clone https://github.com/Pablo-Goros/agent-skills.git "$env:USERPROFILE\.agents"
```

macOS or Linux:

```sh
git clone https://github.com/Pablo-Goros/agent-skills.git "$HOME/.agents"
```

The destination must be absent or empty. If `.agents` already contains files,
back it up outside that directory first, clone the repo, then compare and bring
over any local skills you want to keep. Commit and push those additions so the
other computers receive them too.

## Repository layout

```text
skills/
  skill-name/
    SKILL.md          # Instructions, with name and description in YAML front matter
    agents/           # Optional UI metadata
    references/       # Optional supporting documentation
    scripts/          # Optional executable helpers
    assets/           # Optional templates and other resources
```

Keep each skill's complete folder, including any supporting files stored beside
`SKILL.md`. Use relative links within a skill and home-relative paths in commands
instead of paths tied to a particular username or computer. Keep skill names
unique across your installed skills.

## Scope and dependencies

- This repo tracks personal standalone skills and their supporting files.
- Codex supplies bundled system skills, including `skill-creator` and
  `skill-installer`; they are not copied here.
- Install the plugins you use through Codex on each computer. Plugin caches,
  credentials, account connections, and tool availability are managed separately.
  Copying skill instructions does not install the tools they describe.
- Some skills create or run Bash scripts. Install the required runtime and tools
  on each computer when using those workflows.
- Preserve existing attribution and license files for third-party content. A pull
  from this repo distributes the versions checked in here; it does not fetch
  updates from the skills' original authors. Review and incorporate upstream
  updates here, then commit and push them once.
- Keep secrets and machine-specific configuration outside this repository.
