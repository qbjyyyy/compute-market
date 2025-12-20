⛓️ contracts/ —— 智能合约模块
🎯 模块目标

实现算力交易的链上规则系统，负责资金托管、任务状态管理和事件触发。

📁 关键文件说明
ComputeMarket.sol（核心）

必须实现的功能：

1️⃣ 算力购买

```
function buyCompute(uint256 serviceId) external payable
```

校验支付金额

创建任务 ID

存储任务信息

发出 TaskCreated 事件

2️⃣ 任务状态管理

enum TaskStatus { Created, Running, Completed, Refunded }


只允许合法状态流转

3️⃣ 管理员回调

function completeTask(uint256 taskId, string calldata resultHash) external


仅管理员可调用

更新状态

释放资金

4️⃣ 事件设计（必须）

event TaskCreated(...)
event TaskCompleted(...)
event TaskRefunded(...)

❌ 不要做的事

🚫 不要调用 iExec 合约
🚫 不要在链上存大数据
🚫 不要引入复杂权限系统



⛓️ 智能合约模块（contracts）

定位：链上算力交易与结算规则系统

主要功能包括：

算力购买与支付（ETH）

任务状态管理（Created / Running / Completed / Refunded）

事件触发，驱动链下计算流程

计算完成后的资金结算

⚠️ 合约 不直接执行计算，也不直接调用 iExec 合约，仅作为业务规则与资金托管层。

技术栈：

Solidity

Hardhat

运行
```
npm install
npx hardhat compile
npx hardhat run scripts/deploy.ts --network <network>
```