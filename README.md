# 多电脑互联与远程访问｜Multi-Computer Setup & Remote Access

Set up SSH, VPN, remote desktop access, and remote AI agents across your computers for work at home and on the go.

一台电脑不够用，多台电脑各自为战也不行。这个 skill 帮你把家里的台式机、随身的笔记本和其他电脑连成一个工作网络：从一台机器执行另一台的命令，调用远端 Agent，需要时看屏幕，出门也能接着用。先盘点你有什么设备、想怎么用，再把网络、SSH、远控和供电一起配好。

## 连起来以后可以干什么

- **笔记本借用台式机干活**：“我在笔记本上写东西，想把重任务交给家里的电脑。”先打通 SSH，让命令能到、结果能拿回来。
- **出门继续用自己的电脑**：“帮我把两台电脑连起来，离家也能 SSH 上去。”配好 VPN 入口，在外面也能找到那台机器。
- **几台电脑一起跑 Agent**：“我有三台电脑，想让远端也能跑 Agent，还能看屏幕。”把命令、Agent 和画面分别接通，不用来回搬电脑。
- **手机临时接手**：“我不带电脑时，也想用手机连上家里的工作环境。”按远端 Agent 和手机条件选入口。
- **机器随时能用，屏幕不用常亮**：“电脑屏幕别亮，但我希望随时能远程操作。”把显示器关闭和主机休眠分开设置，再实测唤醒是否可用。

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

## 首次使用：环境自适应

首次触发时，Agent 应只读盘点设备数量、系统、连接方式、是否需要远程屏幕、是否需要远端 Agent，并按设备数量选择方案：1 台无需本 skill，2 台使用最小 SSH + VPN，3 台以上使用完整分层方案并补齐供电策略。真实设备清单经使用者同意后写入 `~/.config/agentops-skills/connect-computers/local-config.md`；无法写该路径时退回 skill 目录内 `local-config.md`；两处都不可写时，本次会话内直接使用盘点结果并提示手动保存。

## 运维方法论

首次配置只是起点。多机长期协作中沉淀的分层思路、无头屏幕方案选择顺序、设备验收清单和配置同步安全边界，见 [operations.md](./operations.md)。

## Changelog

| 时间 | 变更 |
|---|---|
| 2026-07 | 补充多机长期运维方法论 operations.md |
| 2026-07 | 首次开源发布 |

## 反馈与作者

这个 skill 我长期维护。如果你有修改方案、发现问题、或者改出了更好的版本，欢迎通过以下任一渠道找到我：

- GitHub：本仓库提 issue 或 PR
- 小红书：错误乱码
- 微信公众号：能工智人错误乱码
- B站：若逗道人

## 相关 Skill 推荐

<!-- 本表由维护脚本生成，勿手工编辑 -->
- [agent-orchestration](https://github.com/ruodou233/agent-orchestration)：复杂任务跑到半夜，你不可能一直盯着。让 Agent 分工跑长任务和批量工作，你只管第二天早上收结果。<br>Coordinate AI agents for long-running tasks, parallel work, and overnight workflows.
- [upgrade-audit](https://github.com/ruodou233/upgrade-audit)：把你教过 AI 的东西留下来：沉淀偏好、复盘踩坑、更新 skill 和工作流程<br>Review conversation history, agent memory, and skills to identify reusable lessons and propose updates to outdated instructions.
- [claude-cache-keepalive](https://github.com/ruodou233/claude-cache-keepalive)：缓存保温：实测命中、算清收益，让长会话少花冤枉 token<br>Measure prompt cache hits and costs, then configure automatic keepalive when the savings justify it.

完整目录见 [GitHub 主页](https://github.com/ruodou233)。
