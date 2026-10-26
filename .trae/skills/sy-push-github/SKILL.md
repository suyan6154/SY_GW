---
name: "sy-push-github"
description: "Commit and push the whole project to GitHub repo SY_GW. Invoke when user asks to 提交/push/同步项目到 GitHub, or to commit and push changes."
---

# 提交项目到 GitHub（SY_GW）

将本项目的全部变更 commit 并 push 到 GitHub 仓库 `https://github.com/suyan6154/SY_GW.git`（SSH 地址：`git@github.com:suyan6154/SY_GW.git`，SSH 公钥已配置）。

## 执行步骤

1. **检查仓库状态**
   - `git status`：确认有哪些变更；若工作区干净，告知用户无需提交，仅执行 push 同步。
   - `git log --oneline -5`：查看最近提交信息风格，保持一致。

2. **安全检查（提交前必做）**
   - 检查待提交文件中是否包含敏感信息：`.env`、密钥、token、credentials 等。
   - 若发现疑似敏感文件，先向用户确认是否提交，不要擅自提交。

3. **暂存并提交**
   - `git add -A`（本技能的目标是提交整个项目的变更）
   - 用 HEREDOC 方式撰写简洁的提交信息（1-2 句，概括本次变更内容和目的）。
   - 若无任何变更则跳过 commit。

4. **确保 GitHub 远程仓库配置正确**
   - `git remote -v` 检查名为 `github` 的远程是否存在。
   - 若不存在：`git remote add github git@github.com:suyan6154/SY_GW.git`
   - 若存在但 URL 不对：`git remote set-url github git@github.com:suyan6154/SY_GW.git`
   - 注意：**不要修改 `origin`**（origin 指向 Gitee，保留不动）。

5. **推送**
   - 获取当前分支名：`git rev-parse --abbrev-ref HEAD`
   - `git push -u github <当前分支名>`
   - 若被拒绝（远程历史不同），先 `git fetch github` 比较差异并向用户说明；除非用户明确要求，禁止 `--force` 强推。

6. **结果确认**
   - `git status` 确认工作区干净。
   - 向用户报告：提交信息、推送分支、仓库链接 https://github.com/suyan6154/SY_GW

## 注意事项

- 远程地址统一使用 SSH 形式 `git@github.com:suyan6154/SY_GW.git`，不要用 HTTPS（避免重复输入凭据）。
- 禁止使用 `--no-verify` 跳过钩子；禁止未经用户确认的强制推送。
- 若 SSH 认证失败，提示用户运行 `ssh -T git@github.com` 检查公钥配置。
