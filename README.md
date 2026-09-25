# ks-agent-team-collaboration · 多 Agent 协作纪律 🤝

> *Contract-first discipline for multi-agent and multi-team builds.*

同时派五个 agent 写一个项目，是效率的天堂，也是 bug 的温床。

我们实测过一轮端到端测试：**47% 的 bug 只有一个来源——一端改了接口契约，另一端不知道。** 后端把同步接口改成异步返回任务 ID，前端还在等结果；一个字段进了 schema，没有任何人消费它。每个 agent 都「完成了」，合起来跑不通。

这个 skill 就是冲着这 47% 去的。

## 🧱 六条原则，一句话版

1. 🎯 **单一权威状态源** —— 一端算，其他端只派生，不本地猜、不本地缓存
2. 📜 **契约先于代码** —— 改契约必须先改文档，再改代码
3. 🏷️ **影响面强制标注** —— 每个 commit / 每个 agent 总结都要写：我动了对端吗（`frontend-impact: yes/no`）
4. 🗄️ **共享同一份地基** —— 同一数据模型、同一 schema、同一客户端封装，不各搞一套
5. 🚪 **碰别人的领域先打招呼** —— 不确定归属就问，不闷头改
6. 🧵 **变更可追溯** —— 一个 commit 含几批改动就标几批，不漏

## 🚀 派多个 agent 时怎么落地

- fan out 之前，先把它们之间的接口（数据模型、API 形状、共享模块签名）**写进 prompt 当硬约束**
- 每个 agent 只写自己的目录，**共享文件由编排者统一改**
- 让每个 agent 在总结里写「我新增的对外接口 / 我需要的依赖 / 给集成者的注意点」
- 集成时，**专挑模块交界处查**，两端都对

## 💬 你说什么，它给什么

你说：「我要同时派 4 个 agent 分别做登录、订单、支付、通知」

它会先拦你一下：先定四个模块之间的契约，分好不相交的目录，写清谁改主路由、谁改依赖清单，再放 agent 出去。集成那天你会感谢它。

## 📖 来历

从一位 CTO 多年带多人团队 + 多 agent 项目的实践里蒸馏出来。Codex 版额外带 `spawn_agent` 的编排纪律（模型继承、fork_turns、槽位预算）。

## 🧩 搭配

派完要收：[ks-agent-team-review](https://github.com/KaiSky0823/ks-agent-team-review) —— 它专门在交界处找断裂。

## ⚙️ 安装

```bash
# Claude Code
git clone https://github.com/KaiSky0823/ks-agent-team-collaboration.git ~/.claude/skills/ks-agent-team-collaboration
# Codex
git clone https://github.com/KaiSky0823/ks-agent-team-collaboration.git ~/.agents/skills/ks-agent-team-collaboration
```

## License

MIT © 2026 KaiSky0823
