---
name: benchup-skill
description: 在 Windows x64 上使用 BENCHUP 处理用户指定的研究数据，开展论文或数据分析任务，在 Agent 内置网页查看进度和成果；使用官网账号与贝壳。
---

读取本说明后使用编译安装器连接本地科研运行程序，无需预装 Python。

从官网最新清单读取 `installer.download_url` 和 `installer.sha256`，下载并核对后运行。Gitee 仓库如提供同名安装器，也须与清单校验一致；出现需要登录的提示时，使用清单中的 GitHub 地址。GitHub 最新小型安装器入口：

https://github.com/frakzhang0/benchup-releases/releases/download/v3.0.97/BENCHUP-SkillInstall.exe

官网版本清单为 https://benchup.cn/api/public/installation/skill/latest 。其中 `installer.download_url` 与 `installer.sha256` 用于下载和核对最新小安装器。当前 Skill 发布为 3.0.97；安装器先校验已发布的基础运行组件，再应用小型编译差异更新，并逐文件核对最终程序。大运行组件只在首次安装时按需下载，官网不传输组件文件；不发布新的大型整包。首次安装请按真实下载进度等待，不要并发安装。

已有任务先查询状态，任务运行中不要执行 update；等停止后更新，保留原项目、成果与断点。更新前从最新清单重新下载小型安装器，不沿用旧安装器。研究程序没有随本仓库提供源代码。

首次启动（将路径与会话标识替换为实际值）：

    & "<Skill目录>\downloads\BENCHUP-SkillInstall.exe" start --session "<本对话ID>"

读取返回的 `url`，在宿主 Agent 的内置网页中打开工作台。工作台引导用户在 https://benchup.cn 登录或注册并确认连接，再返回本对话。宿主不支持内置网页时说明能力限制并提供链接。密码、验证码和充值操作由用户在官网完成。

科研服务使用官网配置和账号贝壳，无需 Windows 设备授权；宿主 Agent 的聊天模型与科研模型独立。使用安装器的 `status` 查看连接状态，`login --session ID` 可返回授权地址，退出账号用 `logout`。

安装器的 `tasks` 子命令调用已编译的本地任务客户端：

- `tasks projects`：列出可访问的项目，再按返回的会话关联信息核对本对话已有项目，不凭项目名称推测，避免重复创建或启动。
- `tasks create --name NAME --session ID`：为新目标创建项目。
- `tasks import-directory --project ID --root PATH`：仅导入用户指定的研究数据目录；用 `tasks dataset --project ID` 核对完整导入。
- `tasks start --project ID --session ID --goal paper --requirement GOAL`：开展用户要求的论文任务；数据分析可用 `--goal innovation`。仅在用户明确要求建议书时用 `--goal proposal` 并明确研究方向。
- 论文连续多轮在 `tasks start` 后增加 `--total-rounds N`；只在用户指定轮数后设置。用户要求从方案开始时，再加 `--start-step research_plan`。数据分析与建议书模式保留单轮使用。
- `tasks status --project ID`：读取实际执行阶段、错误和成果。
- `tasks resume --project ID --run RUN_ID --session ID --preserve-model-budget`：从选定运行的断点继续，保留历史结果、版本和原额度，不擅自重新授予调用额度或修改轮数。
- `tasks assessment --project ID --run RUN_ID`：查看发表评价。区分当前运行与最近已保存的评价；当前运行尚未评价时，不把历史评价当成本次结果。
- `tasks cancel --project ID --run RUN_ID`：在用户要求停止时使用。

上述命令前都使用同一个安装器路径，例如 `& "<Skill目录>\downloads\BENCHUP-SkillInstall.exe" tasks projects`。端口占用时用独立 `--state PATH --port BASE` 启动；之后 `status`、`login`、`logout`、`stop` 和 `update` 都沿用同一组 `--state PATH --port BASE`，使用自定义 `--program` 时也保持相同。任务命令始终传对应的 `--api http://127.0.0.1:BASE`。更新前先查该环境的任务状态，不能用默认环境的空状态代替。更新用 `update`，安装器先让对应旧程序核实任务已停止，拒绝覆盖正在执行的任务。

提交成功不等于科研完成，报告实际产物和当前阶段。期刊级别评价不代表期刊已接收。按用户要求决定是否生成摘要和引言。错误时读取原因并从原断点恢复，不通过重复创建项目或删除已有结果来绕过问题。
