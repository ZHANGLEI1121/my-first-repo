# GitHub 仓库操作步骤（小白版）

> 适用环境：Windows + PowerShell + GitHub CLI（gh）
> 作者账号：ZHANGLEI1121

---

## 0. 前置准备（只做一次）

1. 打开 __一元客户端__，连上 __香港节点__。
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

> 如果新开的 PowerShell 连不上 GitHub，先给终端临时设代理（端口以客户端显示为准）：

```powershell
$env:HTTP_PROXY  = "http://127.0.0.1:7890"
$env:HTTPS_PROXY = "http://127.0.0.1:7890"
```

---

## 1. 在网页上创建仓库

1. 打开 https://github.com ，确认已登录。
2. 右上角 **+** → New repository。
3. 填写：
   - Repository name：`my-first-repo`（名字自定）
   - Public / Private：公开或私密
   - 勾选 Add a README file
4. 点 **Create repository**。

---

## 2. 把仓库克隆到本地

```powershell
cd D:\我的项目
gh repo clone ZHANGLEI1121/my-first-repo
```

> 生成一个同名文件夹，克隆完成。

---

## 3. 修改 / 添加文件

用记事本或 VSCode 打开仓库文件夹，新建或编辑文件（如 `hello.txt`、`README.md`），保存。

---

## 4. 提交并推送（每次改完都做）

进入仓库文件夹，依次运行：

```powershell
cd D:\我的项目\my-first-repo
git add .
git commit -m "第一次提交"
git push
```

- `git add .`：把所有改动标记上
- `git commit -m "说明"`：给本次改动打标签
- `git push`：上传到 GitHub

完成后刷新 GitHub 页面即可看到更新。

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

## 6. 常见问题

**Q1：新开窗口 gh 连不上 GitHub？**
→ 重新设代理，或保持一元客户端的 TUN/系统代理开启。

**Q2：密码 / 令牌不对？**
→ 浏览器登录时用 GitHub 密码或 Google 登录；忘记密码点 Forgot password。

**Q3：git push 提示没权限？**
→ 先跑 `gh auth login` 重新授权。

**Q4：提交前忘了 cd 到仓库？**
→ 提示 `not a git repository`，先进入仓库文件夹再执行。

---

## 7. 日常流程总结

```
改文件 → git add . → git commit -m "xx" → git push
```

> 小提醒：GitHub 账号是 ZHANGLEI1121，仓库推送前确认在正确的文件夹里。
