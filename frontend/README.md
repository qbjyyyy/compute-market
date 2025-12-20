🖥️ frontend/ —— 前端模块
🎯 模块目标

提供一个完整的 DApp 用户体验，让用户能够安全地购买算力并查看结果。

📁 核心功能
1️⃣ 钱包连接

WalletConnect.vue

MetaMask

显示地址

网络检测

2️⃣ 算力市场页面

Market.vue

算力服务列表

价格展示

购买按钮

3️⃣ 合约交互

services/contract.ts

buyCompute

getTask

4️⃣ 任务列表与状态

Tasks.vue

从后端拉取任务

状态可视化

IPFS 结果展示

❌ 不要做的事

🚫 不处理私钥
🚫 不硬编码合约逻辑
🚫 不直接调用 iExec CLI






🖥️ 前端模块（frontend）

定位：用户交互入口（DApp）

主要功能包括：

MetaMask 钱包连接

显示用户地址与余额

算力服务展示

发起算力购买交易（用户签名）

实时展示任务执行状态

展示计算结果（IPFS）

技术栈：

Vue

Ethers.js

MetaMask