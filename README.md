# BENCHUP 安装入口

当前版本：**Windows 客户端 3.0.96 · Agent Skill 3.0.97**。这里只提供安装说明、小型编译安装器及校验信息，不提供科研源码、用户数据或密钥。

| 使用方式 | 适合谁 | 入口 |
| --- | --- | --- |
| Windows 客户端 | 直接打开独立研究工作台 | 运行 BENCHUP-Installer.exe |
| Agent Skill | 在 WorkBuddy 等 Agent 的对话与内置网页中研究 | 读取 SKILL.md，运行 BENCHUP-SkillInstall.exe |

两种方式都在本机计算，使用官网账号与科研服务。Skill 使用账号＋贝壳，无需 Windows 设备授权；宿主 Agent 自己的聊天费用由宿主决定。

官网安装说明和版本比较：[下载与安装](https://benchup.cn/download/)。

## 下载与校验

- [Windows 最新清单](https://benchup.cn/api/public/installation/windows/latest)
- [Skill 最新清单](https://benchup.cn/api/public/installation/skill/latest)
- [Windows 3.0.96 小型安装器与差异更新](https://github.com/frakzhang0/benchup-releases/releases/tag/v3.0.96)
- [Skill 3.0.97 小型安装器与差异更新](https://github.com/frakzhang0/benchup-releases/releases/tag/v3.0.97)
- [Gitee Windows 安装入口](https://gitee.com/castalzhang/bench-up)
- [Gitee Skill 安装入口](https://gitee.com/castalzhang/benchup-skill)

按清单中的 `installer.download_url` 下载，并核对 `installer.sha256`。首次安装下载已有基础运行组件，再应用最新差异更新。Gitee 提供安装说明和入口；二进制下载以官网清单为准。如果 Gitee 提示大文件需要登录，使用清单中的 GitHub 地址。基础组件与差异更新来自 GitHub Releases，需要能访问该站点。官网不承担大型组件流量，不上传新的大型安装包。

## 让 Agent 安装 Skill

GitHub 安装提示词：

> 请从 https://github.com/frakzhang0/benchup-releases 读取 SKILL.md，在本机安装 BENCHUP Skill（Windows x64）。从 https://benchup.cn/api/public/installation/skill/latest 读取 installer.download_url 和 installer.sha256，下载并核对 BENCHUP-SkillInstall.exe。用 start --session 指定本对话 ID，在你的内置网页打开返回的工作台，指导我在 https://benchup.cn 登录或注册并确认连接。已有任务先查状态，不覆盖运行中的程序。等我指定数据和研究目标再开始，显示真实进度、图表与成果。

Gitee 安装提示词：

> 请从 https://gitee.com/castalzhang/benchup-skill 读取 SKILL.md，在本机安装 BENCHUP Skill（Windows x64）。从 https://benchup.cn/api/public/installation/skill/latest 读取 installer.download_url 和 installer.sha256，下载并核对 BENCHUP-SkillInstall.exe。用 start --session 指定本对话 ID，在你的内置网页打开返回的工作台，指导我在 https://benchup.cn 登录或注册并确认连接。已有任务先查状态，不覆盖运行中的程序。等我指定数据和研究目标再开始，显示真实进度、图表与成果。

## 本次 Skill 更新

3.0.97 修复 Agent Skill 正常启动时的官网通信；重启沿用同一个安装身份，官网按产品显示记录。Windows 客户端继续使用 3.0.96。设备授权与近期在线状态分开展示，独立版不会因此接入官网控制。

## 更新与保留数据

当前任务结束并关闭程序后再更新。请从最新清单重新下载小型安装器，不沿用之前下载的旧安装器。安装器核对基础文件、差异包和最终程序，不覆盖执行中的程序。项目与科研成果不随安装目录删除。原程序目录有研究数据时，选择独立空目录安装，并保留原数据目录。

Windows 客户端运行安装器，按提示选择程序目录。Skill 首次运行 `BENCHUP-SkillInstall.exe start --session 当前对话ID`，默认环境更新用 `BENCHUP-SkillInstall.exe update`。使用自定义 `--state`、`--port` 或 `--program` 的，后续状态、登录、停止、更新命令保持同组参数；其他命令见 SKILL.md。密码、验证码只在官网填写。
