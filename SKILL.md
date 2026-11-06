---
name: benchup-skill
description: 在 Windows x64 上使用 BENCHUP 处理用户指定的研究数据，开展论文或数据分析任务，在 Agent 内置网页查看进度和成果；使用官网账号与贝壳。
---

读取本说明后使用编译安装器连接本地科研运行程序，无需预装 Python。

Gitee 安装入口的 `downloads/BENCHUP-SkillInstall.exe` 可直接运行；GitHub 入口从下面的地址下载同名程序到 `downloads/`：

https://github.com/frakzhang0/benchup-releases/releases/latest/download/BENCHUP-SkillInstall.exe

官网版本清单为 https://benchup.cn/api/public/installation/skill/latest 。其中 `installer.download_url` 与 `installer.sha256` 用于下载和核对最新小安装器。当前发布为 3.0.95；安装器先校验已发布的基础运行组件，再应用小型编译差异更新，并逐文件核对最终程序。大运行组件只在首次安装时按需下载，官网不传输组件文件；不发布新的大型整包。首次安装请按真实下载进度等待，不要并发安装。

已有任务先查询状态，任务运行中不要执行 update；等停止后更新，保留原项目、成果与断点。研究程序没有随本仓库提供源代码。

首次启动（将路径与会话标识替换为实际值）：

    & "<Skill目录>\downloads\BENCHUP-SkillInstall.exe" start --session "<本对话ID>"

读取返回的 `url`，在宿主 Agent 的内置网页中打开工作台。工作台引导用户在 https://benchup.cn 登录或注册并确认连接，再返回本对话。宿主不支持内置网页时说明能力限制并提供链接。密码、验证码和充值操作由用户在官网完成。

科研服务使用官网配置和账号贝壳，无需 Windows 设备授权；宿主 Agent 的聊天模型与科研模型独立。使用安装器的 `status` 查看连接状态，`login --session ID` 可返回授权地址，退出账号用 `logout`。

安装器的 `tasks` 子命令调用已编译的本地任务客户端：

- `tasks projects`：先查本对话已有项目，避免重复创建或启动。
- `tasks create --name NAME --session ID`：为新目标创建项目。
- `tasks import-directory --project ID --root PATH`：仅导入用户指定的研究数据目录；用 `tasks dataset --project ID` 核对完整导入。
- `tasks start --project ID --session ID --goal paper --requirement GOAL`：开展用户要求的论文任务；数据分析可用 `--goal innovation`。仅在用户明确要求建议书时用 `--goal proposal` 并明确研究方向。
- `tasks status --project ID`：读取实际执行阶段、错误和成果。
- `tasks resume --project ID --run RUN_ID --session ID`：从选定运行的断点继续，保留历史结果与版本。
- `tasks cancel --project ID --run RUN_ID`：在用户要求停止时使用。

上述命令前都使用同一个安装器路径，例如 `& "<Skill目录>\downloads\BENCHUP-SkillInstall.exe" tasks projects`。端口占用时用独立 `--state PATH --port BASE` 启动；任务命令同时传 `--api http://127.0.0.1:BASE`。已有兼容运行程序可直接查询状态；更新用 `update`，安装器先让旧程序核实任务已停止，拒绝覆盖正在执行的任务。

提交成功不等于科研完成，报告实际产物和当前阶段。期刊级别评价不代表期刊已接收。按用户要求决定是否生成摘要和引言。错误时读取原因并从原断点恢复，不通过重复创建项目或删除已有结果来绕过问题。
