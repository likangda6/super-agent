# 使用说明：如何发起一个工单

本仓库用于验证 DeepSeek Super-agent 原型。在 GitHub Issue 中 @ 机器人并描述任务，机器人就会把它当作一个「工单」处理，并在完成后提交 Pull Request。

## 发起新工单

1. 打开仓库的 [Issues](https://github.com/likangda6/super-agent/issues) 页面，点击 **New issue**。
2. 填写标题：用一句话说明要完成的事情，例如「新建 docs/usage.md」。
3. 在正文中 @testAgent-hub，并写清楚要做什么：
   - 目标文件和位置，例如 `docs/usage.md`；
   - 需要写入或修改的内容；
   - 可选的验收标准。
4. 提交 Issue，等待机器人在 Issue 中回复确认。

示例：

```markdown
@testAgent-hub 新建 docs/usage.md，写一段使用说明：怎么发起一个工单
```

## 在已有工单中补充要求

在对应的 Issue 下评论并 @testAgent-hub，即可补充或调整需求，不需要另开 Issue。

## 提交之后会怎样

1. 机器人在 Issue 中回复确认，并开始处理。
2. 它在形如 `agent/<工单名>-<编号>` 的分支上完成修改。
3. 修改以 Pull Request 的形式提交，并在 Issue 中通知你。
4. 由人工审阅 Pull Request 并合并。

## 建议

- 一次工单只做一件事，便于确认结果。
- 需求尽量具体，给出文件名、章节标题和预期内容。
- 不要在 Issue 中粘贴密钥、令牌或其他敏感信息。
- 本仓库仅用于原型验证，请勿用于生产用途。
