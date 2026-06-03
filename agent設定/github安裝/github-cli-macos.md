# 連接 GitHub CLI（macOS）

## 安全原則
- 不把 GitHub token 寫進 Markdown、設定檔或 repo
- commit 前先確認 diff，不無差別提交

---

## 1. 確認已安裝 GitHub CLI

```bash
gh --version
```

若尚未安裝：
```bash
brew install gh
```

---

## 2. 登入 GitHub

```bash
gh auth status          # 先確認目前狀態
gh auth login           # 互動式登入（推薦）
```

登入流程互動選項：
- What account? → **GitHub.com**
- Preferred protocol? → **HTTPS**（一般使用）或 **SSH**（有 SSH key 者）
- How to authenticate? → **Login with a web browser**

瀏覽器會開啟，複製終端機顯示的一次性代碼，在瀏覽器完成授權。

```bash
gh auth status          # 驗證成功
```

若需要切換帳號：
```bash
gh auth logout
gh auth login
```

---

## 3. 設定 Git 使用者

```bash
git config --global user.name "你的名字"
git config --global user.email "your-email@example.com"
```

> **不想公開個人信箱**：前往 GitHub → Settings → Emails，開啟
> *Keep my email addresses private*，複製頁面顯示的 no-reply 地址
>（格式：`ID數字+帳號名@users.noreply.github.com`），貼到上面的 email 欄位。

---

## 確認設定

```bash
git config --global --list | grep user
gh auth status
```
