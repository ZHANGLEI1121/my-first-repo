# GitHub 仓库操作步骤（小白版）

> 适用环境：Windows + PowerShell + GitHub CLI（gh）
> 作者账号：ZHANGLEI1121
> 项目路径：E:\我的项目\my-first-repo

---

## 0. 前置准备（只做一次）

1. 打开 `一元客户端`，连上 `香港节点`。
2. 开启「虚拟网卡 TUN」或「系统代理」，确保能访问 GitHub。
3. 在 PowerShell 登录 GitHub CLI：

```powershell
gh auth login
```

4. 按提示选择：
   - Where do you use GitHub? → GitHub.com
   - Preferred protocol → HTTPS
   - Authenticate GitHub credentials → Yes
   - Authenticate → Login with a web browser
5. 复制终端里的一次性代码，在打开的浏览器页面输入并授权。
6. 看到 `Logged in as ZHANGLEI1121` 即成功。

> 新开的 PowerShell 连不上 GitHub 时，先设代理（端口以客户端显示为准）：

```powershell
$env:HTTP_PROXY  = "http://127.0.0.1:7890"
$env:HTTPS_PROXY = "http://127.0.0.1:7890"
```

---

## 1. 创建仓库

- 网页：登录 github.com → `+` → New repository → 填名字、选 Public/Private、勾选 README → Create repository
- 命令：`gh repo create my-first-repo --public --add-readme --description "我的第一个仓库"`

---

## 2. 克隆到本地（本项目在 E 盘）

```powershell
mkdir E:\我的项目
cd E:\我的项目
gh repo clone ZHANGLEI1121/my-first-repo
```

---

## 3. 修改 / 添加文件

用记事本或 VSCode 打开 `E:\我的项目\my-first-repo` 文件夹，新建或编辑文件后保存。

---

## 4. 提交并推送（每次改完都做）

```powershell
cd E:\我的项目\my-first-repo
git add .
git commit -m "说明这次改了什么"
git push
```

- `git add .`：把所有改动标记上
- `git commit -m "说明"`：给本次改动打标签
- `git push`：上传到 GitHub

---

## 5. 常用命令速查

| 目的 | 命令 |
| --- | --- |
| 查看登录状态 | `gh auth status` |
| 看仓库 | `gh repo view 用户名/仓库名` |
| 克隆仓库 | `gh repo clone 用户名/仓库名` |
| 看所有改动 | `git status` |
| 看改动内容 | `git diff` |
| 提交 | `git commit -m "说明"` |
| 推送到 GitHub | `git push` |
| 拉取最新代码 | `git pull` |
| 看提交历史 | `git log --oneline` |
| 看 PR 列表 | `gh pr list` |
| 看 PR 详情 | `gh pr view 编号` |
| 建 issue | `gh issue create` |

---

## 6. GitHub 收费说明（重要）

- **普通仓库、看代码、看提交、建 issue、评审 PR：全部免费**
- 建议用 **Public（公开）** 仓库，完全免费无限制
- Private（私密）个人用也免费，人多协作才可能受限
- 单个文件别超过 100MB；别放视频、大文件
- **GitHub Copilot Pro（每月 $10）是可选 AI 助手，不是必需**，千万别误点订阅

---

## 7. 常见问题

**Q1：新开窗口 gh 连不上？**
→ 重设代理，或保持一元客户端的 TUN/系统代理开启。

**Q2：密码 / 令牌不对？**
→ 浏览器用 GitHub 密码或 Google 登录；忘记密码点 Forgot password。

**Q3：git push 提示没权限？**
→ 先跑 `gh auth login` 重新授权。

**Q4：提示 not a git repository？**
→ 先 `cd` 进入仓库文件夹再执行。

---

## 8. 每日流程总结

```
改文件 → git add . → git commit -m "xx" → git push
```

## 9. 把笔记存进 Obsidian

把本项目仓库里的 `.md` 文件复制到 Obsidian 库（如 `D:\Vault\Obsidian`）即可；Obsidian 会自动识别显示。

> 小提醒：仓库推送前，确认已在 `E:\我的项目\my-first-repo` 文件夹里。
