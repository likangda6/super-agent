# 常见问题（FAQ）

本仓库是 DeepSeek Super-agent 研究原型的沙盒测试仓库，仅用于路由与执行器验证，不用于生产环境。下面五条 FAQ 分别说明收费、渠道、失败、权限和数据，每条附一条 GitHub CLI 命令。运行前请先安装 `gh` 并执行 `gh auth login` 登录。

## 1. 使用需要收费吗？

不收费。本仓库是研究原型沙盒，没有付费套餐、订阅或按次计费，提交工单、生成分支和 Pull Request 都不产生费用，也没有需要付费解锁的高级功能。GitHub API 在免费额度内即可完成日常使用，超出额度时只会被限流，不会被扣费；遇到限流可稍后重试。如果你通过其他账号或第三方服务访问本仓库，是否收费以该服务自己的说明为准。可用下面的命令确认仓库是公开、可免费访问的测试仓库。

```bash
gh repo view likangda6/super-agent --json name,isPrivate,visibility
```

## 2. 支持哪些渠道提交任务？

目前支持 GitHub 一个渠道：在 Issue 正文中 @testAgent-hub 提交新工单，或在已有 Issue、Pull Request 下评论追问，机器人会把确认、进度和改动写回同一线程。仓库暂不提供网页表单、邮件或即时通讯入口，其他渠道提交的需求不在本仓库的处理范围内。一个 Issue 只写一个目标，处理结果更清晰。下面命令可直接创建一个示例工单，创建后打开输出的链接即可查看处理进度。

```bash
gh issue create --repo likangda6/super-agent --title "新建 docs/example.md" --body "@testAgent-hub 新建 docs/example.md，写一段示例说明"
```

## 3. 任务失败了怎么办？

先看 Issue 或 PR 中机器人的最后回复和 CI 状态，确认是需求不清、环境问题还是检查失败。临时性错误直接在原 Issue 评论「重试」并 @testAgent-hub；需求不清则补充目标文件、章节和验收标准后重新提交。连续失败时把任务拆成更小的 Issue，便于定位问题；如果是权限或环境问题，可等维护者恢复后再重试。下面命令可查看 Pull Request 各项检查的状态，快速找出失败项。

```bash
gh pr checks <PR 编号> --repo likangda6/super-agent
```

## 4. 机器人需要什么权限？

机器人以协作者账号 testAgent-hub 运行，需要对仓库拥有 Issues、Pull requests 和 Contents 的读写权限，才能在工单中回复、创建 `agent/` 分支并提交 PR。它不需要仓库管理员权限，也不会向你索取个人令牌。若工单长期没有响应，可先用下面命令检查机器人在仓库中的权限级别；返回 write 表示权限正常，返回 none 或报错则表示权限不足，需要维护者重新授权。

```bash
gh api repos/likangda6/super-agent/collaborators/testAgent-hub/permission
```

## 5. 数据保存在哪里？

任务产生的数据都保存在 GitHub 上：Issue 和 Pull Request 的正文、评论，机器人创建的分支、提交以及 PR diff，均可在对应页面查看，仓库不另设数据库。请在工单中避免粘贴密钥、令牌等敏感信息；删除 Issue 或 Pull Request 后，相关对话在公开页面不再可见。如需长期保留，建议在本地另存一份。下面命令可查看某条工单的完整讨论记录，便于追溯上下文。

```bash
gh issue view 17 --repo likangda6/super-agent --comments
```
