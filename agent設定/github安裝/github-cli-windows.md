# 連接 GitHub CLI（Windows）

## 安全原則
- 不把 GitHub token 寫進 Markdown、設定檔或 repo
- commit 前先確認 diff，不無差別提交

---

## 1. 確認已安裝 GitHub CLI

在 **PowerShell** 執行：

```powershell
gh --version
```

若尚未安裝，擇一方式：
```powershell
winget install --id GitHub.cli      # 推薦
# 或
scoop install gh
# 或
choco install gh
```

安裝後重新開啟 PowerShell 再繼續。

---

## 2. 登入 GitHub

> **注意**：登入流程需要互動式終端機。請在一般 PowerShell 視窗執行，
> 不要在非互動環境（如腳本、管線）中執行。

```powershell
gh auth status          # 先確認目前狀態
gh auth login           # 互動式登入（推薦）
```

登入流程互動選項：
- What account? → **GitHub.com**
- Preferred protocol? → **HTTPS**（一般使用）或 **SSH**（有 SSH key 者）
- How to authenticate? → **Login with a web browser**

終端機會顯示一次性代碼，按 Enter 開啟瀏覽器後輸入代碼完成授權。

```powershell
gh auth status          # 驗證成功
```

若需要切換帳號：
```powershell
gh auth logout
gh auth login
```

---

## 3. 設定 Git 使用者

```powershell
git config --global user.name "你的名字"
git config --global user.email "your-email@example.com"
```

> **不想公開個人信箱**：前往 GitHub → Settings → Emails，開啟
> *Keep my email addresses private*，複製頁面顯示的 no-reply 地址
>（格式：`ID數字+帳號名@users.noreply.github.com`），貼到上面的 email 欄位。

---

## 確認設定

```powershell
git config --global --list | Select-String "user"
gh auth status
```
