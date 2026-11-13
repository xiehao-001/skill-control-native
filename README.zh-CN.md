# 技能可用性策略（@chatecnu-work/dsh-skill-control-native）

> 在官方技能提供者外再套一层可用性策略：按凭据、机构账号与工作区策略决定技能是否可用。
>
> Wraps the filesystem skill provider with credential-, account- and workspace-based availability policy.

## 功能

保留官方解析器、目录优先级、文件监听与作用域语义；在工作区策略之前应用 DSH 设置里的禁用技能名单。可用于“未登录机构账号就不显示文献/邮件技能”这类门控。

## 安装

```bash
# 在 DSH 中把本目录作为本地 bundle 安装（绝对路径）
```

安装后由 DSH 插件系统加载，条目 id 为 `skill-control-native`。

## 依赖

- `@chatecnu-work/dsh-skill-settings-native`
- `@deepseek-ai/cordis`
- `@deepseek-ai/dsh-credentials`
- `@deepseek-ai/dsh-settings`
- `@deepseek-ai/dsh-skill`
- `@deepseek-ai/dsh-skill-filesystem`

## 兼容性

- `engines.dsh`: `>=0.2.1 <0.3.0`
- 与 EduWork 发行版同源，来源于 ECNU/EduWork 仓库。

## 许可

MulanPSL-2.0 AND MIT（与上游 EduWork 一致）。
