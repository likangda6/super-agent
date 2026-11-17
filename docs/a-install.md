# 安装

本仓库是 DeepSeek Super-agent 研究原型的沙盒测试仓库，以文档为主，**不用于生产环境**。克隆后无需安装应用依赖，本地只需准备下面列出的基础环境。

## 环境要求

- Node.js 22.19 或更高版本
- pnpm
- Git

用以下命令检查 Node.js 版本：

```bash
node --version
```

输出 `v22.19.0` 或更高版本即满足要求。

## 安装命令

克隆仓库并在仓库根目录启用 pnpm（Corepack 随 Node.js 提供）：

```bash
git clone https://github.com/likangda6/super-agent.git && cd super-agent && corepack enable
```

当前仓库以文档为主，没有应用依赖，克隆后即可开始使用。

## 验证方法

检查 pnpm 是否可用：

```bash
pnpm --version
```

输出 pnpm 的版本号即表示安装成功。
