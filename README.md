# connect-computers

一台电脑不够用，多台电脑各自为战也不行。这个 skill 帮你用 VPN + SSH 隧道把所有电脑连成一个整体，共享算力和 Agent 能力，你甚至可以用手机远程控制任何一台电脑上的任何 Agent。

## 这是什么 / 解决什么问题

当你有两台以上电脑，问题往往不是“装一个远控软件”就结束：命令执行、屏幕查看、远端 Agent、手机访问和供电策略是不同层的问题。这个 skill 帮你的 Agent 先盘点设备，再按设备数量选择最小可行方案或完整分层方案。它强调 SSH 和 VPN 作为稳定入口，远程屏幕只在需要画面时使用。真实设备清单、账号、IP、SSH alias 和远控 ID 只进入本地配置，不进入可分享文档。

## 核心功能/亮点

- 把网络层、命令层、屏幕层、Agent 层、手机层、供电层分开设计和验收。
- 2 台设备走最小 SSH + VPN，3 台以上走完整分层方案。
- 明确哪些信息不能复制或公开：密钥、token、session、浏览器 Cookie、真实设备清单。
- 将 Wake-on-LAN 视为需实测的备用能力，而不是可靠性的默认前提。
- 提供 `local-config.example.md`，方便把真实设备清单隔离在本地。

## 安装

Claude Code：

```bash
git clone https://github.com/ruodou233/connect-computers.git ~/.claude/skills/connect-computers
```

Codex：

```bash
git clone https://github.com/ruodou233/connect-computers.git ~/.agents/skills/connect-computers
```

其他支持 SKILL.md 的平台：放入其 skills 目录即可。

## 使用示例

- “帮我把两台电脑连起来，离家也能 SSH 上去。”预期行为：先只读盘点两台设备，再给出最小 SSH + VPN 方案和验收步骤。
- “我有三台电脑，想让远端也能跑 Agent，还能看屏幕。”预期行为：按网络、命令、屏幕、Agent、供电分层设计，并提醒真实设备清单只写本地配置。
- “电脑屏幕别亮，但我希望随时能远程操作。”预期行为：优先建议关闭显示器但不让主机睡眠，再讨论是否需要 Wake-on-LAN 备用。

## 首次使用：环境自适应

首次触发时，Agent 应只读盘点设备数量、系统、连接方式、是否需要远程屏幕、是否需要远端 Agent，并按设备数量选择方案：1 台无需本 skill，2 台使用最小 SSH + VPN，3 台以上使用完整分层方案并补齐供电策略。真实设备清单经使用者同意后写入 `~/.config/agentops-skills/connect-computers/local-config.md`；无法写该路径时退回 skill 目录内 `local-config.md`；两处都不可写时，本次会话内直接使用盘点结果并提示手动保存。

## Changelog

| 时间 | 变更 |
|---|---|
| 2026-07 | 首次开源发布 |

## 反馈与作者

这个 skill 我长期维护。如果你有修改方案、发现问题、或者改出了更好的版本，欢迎通过以下任一渠道找到我：

- GitHub：本仓库提 issue 或 PR
- 小红书：错误乱码
- 微信公众号：能工智人错误乱码
- B站：若逗道人

## 相关 Skill 推荐

<!-- 本表由维护脚本生成，勿手工编辑 -->
- [agent-orchestration](https://github.com/ruodou233/agent-orchestration)：长任务/过夜流程编排，Agent 自主跑、自主省 token，不用你盯
- [upgrade-audit](https://github.com/ruodou233/upgrade-audit)：AI 每天自主升级知识体系，教一遍就会，不用反复纠正
- [claude-cache-keepalive](https://github.com/ruodou233/claude-cache-keepalive)：缓存保温策略，最高可压低 90% token 消耗，各种 Agent 通用

完整目录见 [GitHub 主页](https://github.com/ruodou233)。
