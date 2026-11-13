# Skill Control: Credential and Workspace Gating

`@chatecnu-work/dsh-skill-control-native` · v0.1.0-dev · MulanPSL-2.0 AND MIT

Skill Control wraps the official filesystem skill provider with an availability policy, so a deployment can decide which skills are offered based on credentials, institutional account bindings and workspace policy. It is aimed at managed EduWork deployments where, for example, literature or mail skills must stay hidden until the user signs in with an institutional account.

The plugin keeps the official provider semantics and only adds a policy layer in front of them. Disabled-skill preferences from DSH settings are applied before workspace policy, so the same preference set governs every workspace.

## Highlights

- Wraps the official filesystem skill provider instead of replacing it, preserving official resolution, directory priority, file watching and scope semantics.
- Applies the DSH settings-plane disabled-skill list before workspace policy, so one preference set governs every workspace.
- Checks credential presence, account-binding availability and required capabilities before a skill is offered.
- Shares the `chatecnu-skills` settings namespace with `@chatecnu-work/dsh-skill-settings-native`, so the settings screen and the gate read the same records.
- Ships the policy core as a separate `./core` entry next to the plugin entry point.
- Fits "hide literature and mail skills until institutional sign-in" deployments without forking the host's skill loader.

## Install

Install this directory as a local DSH plugin bundle. From a shell:

```bash
dsh plugin --profile web add /absolute/path/to/skill-control-native
```

Or add the directory through the **Plugins** panel in DSH (local bundle). Restart the DSH app after installation; plugins are activated from the bundle patch (`cordis.patch.yml`).

## Configuration

No configuration keys are shipped here: the bundle patch inserts the plugin with defaults. The host half still honors `skillDir`, `providerName` and `customSkillDirs` if they are added to the plugin config, and `skillDir` may instead come from the `DSH_BUNDLED_SKILL_DIR` environment variable.

## Requirements

- DeepSeek Harness `>=0.2.1 <0.3.0`
- Peer packages: `@chatecnu-work/dsh-skill-settings-native`, `@deepseek-ai/cordis`, `@deepseek-ai/dsh-credentials`, `@deepseek-ai/dsh-settings`, `@deepseek-ai/dsh-skill`, `@deepseek-ai/dsh-skill-filesystem`

## Notes and limits

- The host half refuses to start when no skill directory is resolved: set `skillDir` in the plugin config or `DSH_BUNDLED_SKILL_DIR` in the environment. The shipped bundle patch has an empty `config: {}`.
- The settings namespace is owned by `@chatecnu-work/dsh-skill-settings-native`; install that package for host-owned, durable preferences.
- Version `0.1.0-dev` is a development-stage release.

## 中文文档

[README.zh-CN.md](./README.zh-CN.md)

## License

MulanPSL-2.0 AND MIT — see [LICENSE](./LICENSE) and, where present, [LICENSE-MIT](./LICENSE-MIT). Extracted from the ECNU EduWork distribution (https://github.com/ECNU/EduWork); upstream copyright and license notices are preserved.
