# 連接 NotebookLM ↔ Antigravity（macOS）

## 安全原則
- 登入走瀏覽器 OAuth，不複製 cookie / token
- 不把 notebooks.json 或筆記本 ID 清單放進 repo

---

## 1. 安裝 notebooklm-mcp-cli

```bash
# 優先用 uv（推薦）
uv tool install notebooklm-mcp-cli

# 沒有 uv 則改用 pipx
pipx install notebooklm-mcp-cli

# 最後備選
pip install notebooklm-mcp-cli
```

確認安裝：
```bash
nlm --version
```

> 若 `nlm` 找不到，將 `~/.local/bin` 加入 PATH：
> ```bash
> echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
> ```

---

## 2. Google 帳號授權

```bash
nlm login
# 瀏覽器會開啟，選擇正確的 Google 帳號完成 OAuth
```

若需要切換帳號：
```bash
nlm logout && nlm login
```

驗證：
```bash
nlm doctor
nlm notebook list   # 確認能看到筆記本，但勿 commit 清單
```

---

## 3. 一鍵註冊 MCP 到 Antigravity

```bash
nlm setup add antigravity
```

此指令會自動寫入正確的設定檔位置，**不需要手動編輯 JSON**。

完成後重啟 Antigravity，請它列出 NotebookLM 筆記本，只回報是否成功即可。

---

## 更新套件

```bash
uv tool upgrade notebooklm-mcp-cli
# 或
pipx upgrade notebooklm-mcp-cli
```
