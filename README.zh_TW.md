# GitLab for Stream Deck

[Español](README.es.md) · [English](README.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [简体中文](README.zh_CN.md) · **繁體中文**

用於監控與控制 GitLab.com 或自架實例流水線、顯示 MR/Issue 計數、開啟專案頁面並複製常用資料的 Stream Deck 外掛。

## 需求

- Stream Deck 7.1+
- 具有 **api** 權限的 Personal Access Token

## 帳戶（全域）

權杖在外掛層級只儲存一次，並在所有動作中重用：

1. 在任意動作中開啟 **Manage accounts…** 或選擇 **Add accounts**。
2. 填寫 **Name**、**Token** 與 **Domain**（選填，自架；預設 `https://gitlab.com`）。
3. 在每個按鍵上從 **Account** 下拉選單選擇帳戶。

可設定多個帳戶（例如 GitLab.com + 自架）。

---

## 動作

### Pipeline Status

最新流水線的即時狀態（success、pending、running、failed、canceled）。處於 **RUNNING** 時，偵測到執行後計時器從 `00:00:00` 開始。

| 按鍵 | 行為 |
|---|---|
| **短按** | 依狀態：重新整理（`success` / `pending` / idle / `canceled`）；開啟流水線（`running`）；開啟失敗的 job（`failed`） |
| **長按**（約 0.6 秒） | 取消（`pending` / `running`）；重試失敗的 job（`failed`）；重試流水線（`canceled`） |

**設定**

| 欄位 | 說明 |
|---|---|
| Account | GitLab 帳戶 |
| Project | 路徑 `group/repo` 或數字 ID |
| Branch / ref | 選填；過濾最新流水線 |
| Poll (sec) | 重新整理間隔（5–120；預設 15） |

---

### Open Pipeline

顯示最新流水線編號（`#N`）。

| 按鍵 | 行為 |
|---|---|
| **點擊** | 在瀏覽器開啟最新流水線 |

**設定：** Account、Project、Branch / ref（選填）。

---

### Run Pipeline

| 按鍵 | 行為 |
|---|---|
| **點擊** | 在指定分支建立新流水線（Branch 空白則使用專案預設分支） |

**設定：** Account、Project、Branch / ref（選填）。

---

### Retry Pipeline

| 按鍵 | 行為 |
|---|---|
| **點擊** | 重試最近一次**失敗**的流水線（可依分支過濾） |

**設定：** Account、Project、Branch / ref（選填）。

---

### Cancel Pipeline

| 按鍵 | 行為 |
|---|---|
| **點擊** | 在可取消時取消最新流水線（`running`、`pending` 等） |

**設定：** Account、Project、Branch / ref（選填）。

---

### Merge Requests

開啟中的合併請求計數。標籤為 `MR`（全部）或 `MY MR`（指派給你）。

| 按鍵 | 行為 |
|---|---|
| **點擊** | 在瀏覽器開啟 MR 列表（若為 “Assigned to me” 則帶過濾） |

**設定**

| 欄位 | 說明 |
|---|---|
| Account | GitLab 帳戶 |
| Project | 專案路徑或 ID |
| Count scope | **All open** = 全部開啟；**Assigned to me** = 指派給權杖使用者 |
| Poll (sec) | 重新整理間隔（最少 15 秒；預設 30） |

---

### Issues

開啟中的 Issue 計數。標籤為 `ISSUES` 或 `MY ISSUES`。

| 按鍵 | 行為 |
|---|---|
| **點擊** | 在瀏覽器開啟 Issue 列表（必要時帶過濾） |

**設定：** 與 Merge Requests 相同（Account、Project、Count scope、Poll）。

---

### Open Repository

| 按鍵 | 行為 |
|---|---|
| **點擊** | 開啟專案 / 儲存庫頁面 |

**設定：** Account、Project。按鍵標題顯示簡短儲存庫名稱。

---

### Jobs Status

最新流水線的 Job 狀態，例如 `8/10 ✓`（或依狀態顯示 `✗` / `…`）。

| 按鍵 | 行為 |
|---|---|
| **點擊** | 重新整理計數 |

**設定：** Account、Project、Branch / ref（選填）、Poll (sec)。

---

### Failed Job

顯示失敗的 Job 名稱（`FAILED` + 名稱；若無失敗則為 `OK`）。

| 按鍵 | 行為 |
|---|---|
| **點擊** | 在瀏覽器開啟失敗 Job 的記錄 |

**設定：** Account、Project、Branch / ref（選填）、Poll (sec)。

---

### Copy Branch Name

| 按鍵 | 行為 |
|---|---|
| **點擊** | 將設定的分支、最新流水線分支或預設分支複製到剪貼簿 |

**設定：** Account、Project、Branch / ref（選填）。標題顯示分支名稱。

---

### Copy Repository URL

| 按鍵 | 行為 |
|---|---|
| **點擊** | 將 clone URL（HTTP 或 SSH）複製到剪貼簿 |

**設定**

| 欄位 | 說明 |
|---|---|
| Account | GitLab 帳戶 |
| Project | 專案路徑或 ID |
| URL kind | **HTTP** 或 **SSH** |

---

### Open Environments

| 按鍵 | 行為 |
|---|---|
| **點擊** | 開啟專案的 `/-/environments` |

**設定：** Account、Project。固定標題：`Env`。

---

### Open CI/CD

| 按鍵 | 行為 |
|---|---|
| **點擊** | 開啟專案的 `/-/pipelines` |

**設定：** Account、Project。固定標題：`CI/CD`。

## 支持

☕ **請我喝杯咖啡**  
如果這個外掛幫你節省了時間，可以在這裡支持開發：  
https://paypal.me/danielpradom
