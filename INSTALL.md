# Install InfinityBlade

InfinityBlade is a portable Agent Skill. Copy `skills/infinityblade` into the skill directory supported by your agent host.

## Codex

Copy the folder to:

```text
~/.codex/skills/infinityblade/
```

Start a new session, then invoke:

```text
Use $infinityblade to complete this repair.
```

The skill may also activate automatically for relevant implementation, debugging, deployment, automation, and verification tasks.

For repository-level enforcement, retain `AGENTS.md` and the linked skill folder in the target repository.

## Other Agent Skill hosts

Install `skills/infinityblade` using the host's Agent Skills location or importer. Keep `SKILL.md` and `references` together. For instruction-only hosts, adapt `AGENTS.md` to the host's repository instruction filename.

## Confirm discovery

Ask:

```text
Use $infinityblade. State the five SCOPE fields for this task before making a material change.
```

Correct discovery produces Surface, Constraints, Outcome, Proof, and Edges, followed by evidence-matched completion reporting.

For a quick behavior check after installation or an update, run the representative activation, non-activation, incomplete-input, and safety cases in [`skills/infinityblade/references/eval-cases.md`](skills/infinityblade/references/eval-cases.md).

