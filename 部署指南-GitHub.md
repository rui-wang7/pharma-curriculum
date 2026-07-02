# 手把手：用 GitHub 发布网站（GitHub Desktop 图形版）

> 目标：把这个文件夹传到 GitHub，再让 Vercel 连上它自动上线。以后你每次改动，点一下就自动更新网站。
> 全程几乎不用命令行。遇到任何一步卡住，截图发我。约 15 分钟。

---

## 第 0 步：先清掉一个残留文件（重要）
生成环境在文件夹里留了个半成品的隐藏 `.git`，不清掉会让 GitHub Desktop 犯迷糊。清理方法二选一：

**方法一（推荐，最稳）：** `⌘ + 空格` 打开 **终端 Terminal**，输入 `cd ` 加一个空格，把 **Pharma curriculum 文件夹从访达拖进终端**，回车；再粘贴这行回车：
```bash
rm -rf .git .vercel
```
（看不到任何输出就是成功了。）

**方法二（不想碰终端）：** 在访达里进入这个文件夹，按 `⇧ + ⌘ + .`（Shift+Command+句号）显示隐藏文件 → 把灰色的 `.git` 文件夹拖进废纸篓 → 再按一次 `⇧ + ⌘ + .` 隐藏回去。

---

## 第 1 步：注册 GitHub 账号（已有就跳过）
1. 打开 https://github.com → 点 **Sign up**。
2. 按提示填邮箱、密码、用户名 → 去邮箱点验证邮件。

## 第 2 步：装 GitHub Desktop
1. 打开 https://desktop.github.com → 下载 **macOS** 版 → 把它拖进"应用程序"。
2. 打开 GitHub Desktop → 点 **Sign in to GitHub.com** → 用刚才的账号登录（会跳一下浏览器授权，点同意）。
3. 登录后如果问 "Name / Email" 配置，直接用默认，点 Continue / Finish。

## 第 3 步：把文件夹变成一个仓库
1. 顶部菜单 **File → Add Local Repository…**
2. 点 **Choose…**，选中 **Pharma curriculum** 这个文件夹，打开。
3. 它会提示："This directory does not appear to be a Git repository. **Create a Repository?**" → 点蓝字 **create a repository**。
4. 弹窗里 **Name** 会自动填好（如 `Pharma curriculum`，可改成 `pharma-curriculum`），其它不用动 → 点 **Create Repository**。

## 第 4 步：发布到 GitHub
1. 现在窗口右上角会出现 **Publish repository** 按钮，点它。
2. 弹窗里：
   - **Keep this code private**：想让别人搜不到就**勾上**（推荐）；想公开就取消勾选。
   - 其它默认。
3. 点 **Publish repository**。几秒后，你的代码就在 GitHub 上了。✅

> 检验：菜单 **Repository → View on GitHub**，浏览器会打开你的仓库，能看到 `index.html`、`dict/`、`assets/` 等文件就对了。

## 第 5 步：让 Vercel 连上它、自动上线
1. 打开 https://vercel.com → 点 **Sign Up / Log in** → 选 **Continue with GitHub** → 授权。
2. 进入后点 **Add New… → Project**。
3. 在列表里找到刚发布的仓库（如 `pharma-curriculum`）→ 点它右边的 **Import**。
   - 若没看到：点 **Adjust GitHub App Permissions**，把该仓库授权给 Vercel。
4. 配置页什么都不用改：**Framework Preset** 选 **Other**（纯静态网站，无需 build）。
5. 点 **Deploy**，等进度条跑完（约半分钟）。
6. 出现 🎉 和一个 **Visit** 按钮 → 点开就是你的网站，网址形如 `https://pharma-curriculum.vercel.app`。随时能打开、能分享。

---

## 以后怎么更新网站（关键好处）
每当我帮你把词典又加了内容，你只要：
1. 打开 **GitHub Desktop**（它会自动列出改动的文件）。
2. 左下角写一句说明（如"加了肿瘤耐药机制"）→ 点 **Commit to main**。
3. 顶部点 **Push origin**。
4. 完成——Vercel 检测到改动会**自动重新部署**，同一个网址几十秒后就更新了。不用再碰 Vercel。

---

## 常见卡点
- **GitHub Desktop 里看不到 create a repository 提示**：说明第 0 步没清干净 `.git`，回去清掉再重来。
- **Vercel 导入列表里没有你的仓库**：点 Import 页的 **Adjust GitHub App Permissions**，勾选该仓库授权。
- **部署后打开是 404**：确认 Framework 选的是 **Other**、根目录里有 `index.html`（本项目就在根目录，正常不会 404）。
- **想换更好记的网址**：Vercel 项目 → **Settings → Domains**，可改 `你起的名字.vercel.app` 或绑定自有域名。
- **`COWORK-handoff.md` 没被上传**：正常，`.gitignore` 故意忽略了它，不影响网站。
