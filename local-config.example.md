# connect-computers local-config 示例

本文件用于记录使用者自己的设备清单和本地决策。真实设备名、账号、IP、SSH alias、远控 ID、token、session 等敏感信息只应保存在本地配置中，不要写入可分享文档、README 或 issue。

推荐读取顺序：

1. `~/.config/agentops-skills/connect-computers/local-config.md`
2. skill 目录内 `local-config.md`
3. 无本地配置时，按 `SKILL.md` 的首次使用流程重新只读盘点

填写前，Agent 应先只读盘点设备；写入本文件或等价本地配置前，必须向使用者说明写入位置和内容，并取得明确同意。

## 设备清单

| 设备名 | 系统 | 入口方式 | 是否远端 Agent | 供电策略 |
|---|---|---|---|---|
| 示例-主力本 | macOS 示例版本 | VPN 主机名 + SSH；需要时用 RustDesk | 是 | 显示器 10 分钟关闭，主机不睡眠 |
| 示例-工作站 | Windows 示例版本 | VPN 主机名 + OpenSSH；系统远程桌面备用 | 是 | 常接电，睡眠关闭，断电后手动恢复 |
| 示例-备用机 | Linux 示例发行版 | 内网 SSH；VPN 待配置 | 否 | 节能优先，Wake-on-LAN 待实测 |

## 填写说明

- 设备名：使用本地可识别名称；公开分享前改为泛称或删除。
- 系统：写操作系统和大版本即可，不需要写账号或序列号。
- 入口方式：记录可用入口类别，例如内网 SSH、VPN SSH、RustDesk、RDP、VNC；不要写真实 IP、真实远控 ID 或明文密码。
- 是否远端 Agent：写“是/否/待安装”，并在本地记录登录状态是否已验证。
- 供电策略：写“主机不睡眠”“节能优先 + Wake-on-LAN”“手动开机”等可执行策略，并标注是否已经实测。

## 本地决策

- 设备数量：
- 推荐方案：
- VPN 方案：
- SSH 验收状态：
- 远程屏幕验收状态：
- 远端 Agent 验收状态：
- 供电验收状态：
