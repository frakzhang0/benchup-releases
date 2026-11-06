# BENCHUP 安装入口

当前版本：**3.0.95**。这里只提供安装说明、小型编译安装器及校验信息，不提供科研源码、用户数据或密钥。

| 使用方式 | 适合谁 | 入口 |
| --- | --- | --- |
| Windows 客户端 | 直接打开独立研究工作台 | 运行 BENCHUP-Installer.exe |
| Agent Skill | 在 WorkBuddy 等 Agent 的对话与内置网页中研究 | 读取 SKILL.md，运行 BENCHUP-SkillInstall.exe |

两种方式都在本机计算，使用官网账号与科研服务。Skill 使用账号＋贝壳，无需 Windows 设备授权；宿主 Agent 自己的聊天费用由宿主决定。

官网安装说明和两种版本的比较：https://benchup.cn/download/

## 下载与校验

- Windows 清单：https://benchup.cn/api/public/installation/windows/latest
- Skill 清单：https://benchup.cn/api/public/installation/skill/latest
- GitHub 小型安装器与差异更新：https://github.com/frakzhang0/benchup-releases/releases/tag/v3.0.95
- Gitee Windows 入口：https://gitee.com/castalzhang/bench-up
- Gitee Skill 入口：https://gitee.com/castalzhang/benchup-skill

按清单中的 installer.download_url 下载，并核对 installer.sha256。首次安装需下载已有基础运行组件，然后校验、应用最新差异更新。Gitee 可下载安装器；完整基础组件仍来自 GitHub Releases，需要能访问该站点。官网不承担大型组件流量。本次未上传新的大型安装包。

## 让 Agent 安装 Skill

把下面一段发给 Agent（GitHub 与 Gitee 安装同一版本）：

> 请从 https://gitee.com/castalzhang/benchup-skill 读取 SKILL.md，按 https://benchup.cn/api/public/installation/skill/latest 下载并核对最新 BENCHUP-SkillInstall.exe。用 start --session 指定本对话 ID，在你的内置网页打开返回的工作台，指导我在 https://benchup.cn 登录或注册并确认连接。保留正在运行的任务，不覆盖安装。等我指定数据和研究目标再开始，显示真实进度、图表与成果。

GitHub 入口可将上文仓库地址替换为 https://github.com/frakzhang0/benchup-releases。

## 更新与保留数据

当前任务结束并关闭程序后再更新。安装器核对基础文件、差异包和最终程序，不覆盖执行中的程序。项目与科研成果不随安装目录删除。已有非基础版本或程序目录内有研究数据时，请选择独立空目录安装，保留原数据目录。

Windows 客户端运行安装器，按提示选择程序目录。Skill 首次运行 `BENCHUP-SkillInstall.exe start --session 当前对话ID`，更新用 `BENCHUP-SkillInstall.exe update`；其他命令见 SKILL.md。密码、验证码只在官网填写。
