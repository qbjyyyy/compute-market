⚙️ backend/ —— 后端模块
🎯 模块目标

监听链上事件，调度 iExec 计算任务，并同步计算状态。

📁 核心职责拆解
1️⃣ 监听合约事件

TaskCreatedListener.java

订阅 TaskCreated 事件

解析 taskId / user / serviceId

创建数据库记录

2️⃣ iExec CLI 调用封装

IexecCliService.java

封装 Shell 命令：

iexec app deploy
iexec deal


返回 iExec taskId

3️⃣ 任务监控

TaskMonitorService.java

定时轮询 iExec 状态

检测 completed

获取 IPFS Hash

4️⃣ 回写合约

TaskService.java

调用 completeTask

更新数据库状态

5️⃣ REST API

TaskController.java

GET /tasks/{userAddress}

GET /tasks/{taskId}

❌ 不要做的事

🚫 不保存私钥到数据库
🚫 不替用户签名交易
🚫 不直接操作用户钱包




⚙️ 后端模块（backend）

定位：链下算力调度与状态同步服务

主要功能包括：

监听智能合约 TaskCreated 事件

调用 iExec CLI 触发真实计算任务

轮询 iExec 网络获取任务状态

获取计算结果（IPFS Hash）

回写任务完成状态到链上

提供 REST API 给前端查询任务状态

后端 不持有用户私钥、不替用户签名交易，仅作为链上与 iExec 网络之间的桥梁。

技术栈：

Spring Boot

Web3j

MySQL

iExec CLI

使用后端服务，确保已正确安装并配置：

iExec CLI

Ethereum RPC 节点

数据库
