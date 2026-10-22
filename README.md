# Agent 自定义规则

集中管理各个 agent 平台的自定义规则，保留修改历史，并在多台设备间同步。

朋友可以直接读取和克隆这个公开仓库。让朋友的 AI 安装或更新全局规则时，复制对应平台的同步指令中的提示词即可：[Codex](docs/codex-sync.md)、[Claude Code](docs/claude-sync.md)。

## 目录

```text
platforms/
  codex/
    AGENTS.md       # 当前 Codex 全局规则
    skills/
      frontend-no-subtitles/  # 按需使用的前端文案精简技能
  claude/
    CLAUDE.md       # 当前 Claude Code 全局规则
```

每个平台使用独立目录，保留该平台原生的规则文件名。新增平台时，在 `platforms/<平台名>/` 中添加实际规则，并在对应目录写明安装位置和生效方式。平台间共享的偏好可以按需同步到各自的规则文件。

## 在另一台设备使用 Codex 规则

先克隆仓库：

```sh
git clone https://github.com/Lidong1793/agent-rules.git
cd agent-rules
```

将 `platforms/codex/AGENTS.md` 复制到目标设备的 Codex 全局目录。目标位置已有规则时，先备份并检查需要合并的内容。

- Windows 默认位置：`%USERPROFILE%\.codex\AGENTS.md`
- macOS / Linux 默认位置：`~/.codex/AGENTS.md`
- 设置了 `CODEX_HOME` 时：`$CODEX_HOME/AGENTS.md`

同一全局目录中的 `AGENTS.override.md` 优先于 `AGENTS.md`。安装后，新建会话并让 Codex 总结当前全局规则，确认加载结果。

官方规则发现说明：https://learn.chatgpt.com/docs/agent-configuration/agents-md

## 按需使用 Codex 技能

将 `platforms/codex/skills/frontend-no-subtitles/` 整个目录复制到 Codex 的 `skills/` 目录：

- Windows：`%USERPROFILE%\.codex\skills\frontend-no-subtitles\`
- macOS / Linux：`~/.codex/skills/frontend-no-subtitles/`
- 设置了 `CODEX_HOME` 时：`$CODEX_HOME/skills/frontend-no-subtitles/`

[frontend-no-subtitles](platforms/codex/skills/frontend-no-subtitles/SKILL.md) 用于按需清理副标题和装饰性文案，保留必要提示、状态和现有功能。它在请求精简界面文案或无副标题设计时适用。

调用示例：

```text
使用 $frontend-no-subtitles 清理当前页面的副标题和冗余文案。
```

## 在另一台设备使用 Claude Code 规则

克隆仓库后，将 `platforms/claude/CLAUDE.md` 复制到目标设备的 Claude Code 全局目录。目标位置已有规则时，先备份并检查需要合并的内容。

- Windows 默认位置：`%USERPROFILE%\.claude\CLAUDE.md`
- macOS / Linux 默认位置：`~/.claude/CLAUDE.md`
- 设置了 `CLAUDE_CONFIG_DIR` 时：`$CLAUDE_CONFIG_DIR/CLAUDE.md`

安装后，新建会话并让 Claude 总结当前全局规则，确认加载结果。让 AI 自动安装时，使用[给 AI 的同步指令](docs/claude-sync.md)。

## 更新规则

1. 修改前运行 `git pull --ff-only`，获取其他设备提交的最新版本。
2. 编辑仓库中对应平台的规则文件；如果在平台本地修改，先将文件同步回仓库。
3. 检查差异，再提交并推送：

   ```sh
   git diff
   git add platforms/
   git commit -m "Update agent rules"
   git push
   ```

4. 其他设备拉取更新，再将规则文件复制到对应平台的实际加载位置。

Git 同步仓库里的文件。各个平台从自己的规则目录读取文件，因此拉取后需要完成复制步骤。

## 收录范围

仓库收录自定义规则和必要的使用说明。账号凭据、访问令牌、会话记录及机器专属配置保存在设备本地。
