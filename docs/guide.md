# Super-agent 使用指南

本仓库是 DeepSeek Super-agent 研究原型的沙盒测试仓库，用于路由与执行器的验证，**不用于生产环境**。本文档包含安装、使用和 FAQ 三部分。

## 安装

### 环境要求

- Node.js 22.19 或更高版本
- pnpm

### 安装步骤

1. 确认 Node.js 版本不低于 22.19：

   ```bash
   node --version
   ```

2. 安装 pnpm（已安装可跳过）：

   ```bash
   corepack enable
   ```

   若环境中没有 Corepack，也可以使用 npm 全局安装：

   ```bash
   npm install -g pnpm
   ```

3. 克隆仓库并进入目录：

   ```bash
   git clone https://github.com/likangda6/super-agent.git
   cd super-agent
   ```

4. 验证安装结果：

   ```bash
   node --version   # v22.19.0 或更高
   pnpm --version
   ```

当前仓库以文档为主，克隆后无需安装额外依赖。如果后续加入应用代码（存在 `package.json`），在仓库根目录执行：

```bash
pnpm install
```

## 使用

Super-agent 通过 GitHub Issue 接收任务（工单）。在 Issue 中 @testAgent-hub 并描述任务，机器人会将其作为工单处理，并在完成后提交 Pull Request。

### 发起一个工单

1. 打开仓库的 [Issues](https://github.com/likangda6/super-agent/issues) 页面，点击 **New issue**。
2. 填写标题：用一句话说明要完成的事情，例如「新建 docs/guide.md」。
3. 在正文中 @testAgent-hub，并写清楚要做什么：
   - 目标文件和位置，例如 `docs/guide.md`；
   - 需要写入或修改的内容；
   - 可选的验收标准。
4. 提交 Issue，等待机器人在 Issue 中回复确认。

示例：

```markdown
@testAgent-hub 新建 docs/guide.md，写三段：安装、使用、FAQ
```

### 在已有工单中补充要求

在对应的 Issue 下评论并 @testAgent-hub，即可补充或调整需求，不需要另开 Issue。

### 提交之后会怎样

1. 机器人在 Issue 中回复确认，并开始处理。
2. 它在形如 `agent/<工单名>-<编号>` 的分支上完成修改。
3. 修改以 Pull Request 的形式提交，并在 Issue 中通知你。
4. 由人工审阅 Pull Request 并合并。

### 建议

- 一次工单只做一件事，便于确认结果。
- 需求尽量具体，给出文件名、章节标题和预期内容。
- 不要在 Issue 中粘贴密钥、令牌或其他敏感信息。
- 本仓库仅用于原型验证，请勿用于生产用途。

## FAQ

### 1. 必须本地安装 Node.js 和 pnpm 吗？

如果只通过 Issue 提交任务，不需要在本地安装任何东西；只有需要在本地运行或验证项目时，才需要准备上述环境。

### 2. 任务完成后在哪里查看结果？

Agent 会在对应的 Issue 或 Pull Request 中回复，并附上 PR 链接。所有改动都可以在 PR 的 **Files changed** 中查看。

### 3. 可以一次提交多个需求吗？

建议拆成多个 Issue。一个 Issue 对应一个明确目标，处理结果更清晰，也更容易审查和合并。
