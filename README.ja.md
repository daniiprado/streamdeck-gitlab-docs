# GitLab for Stream Deck

[Español](README.es.md) · [English](README.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · **日本語** · [한국어](README.ko.md) · [简体中文](README.zh_CN.md) · [繁體中文](README.zh_TW.md)

GitLab.com またはセルフホストのパイプラインを監視・操作し、MR/Issue の件数表示、プロジェクト各画面のオープン、便利なデータのコピーを行う Stream Deck プラグインです。

## 要件

- Stream Deck 7.1+
- スコープ **api** の Personal Access Token

## アカウント（グローバル）

トークンはプラグイン単位で一度だけ保存し、すべてのアクションで再利用します。

1. 任意のアクションで **Manage accounts…** を開くか **Add accounts** を選ぶ。
2. **Name**、**Token**、**Domain**（任意、セルフホスト。既定は `https://gitlab.com`）を入力。
3. 各キーで **Account** ドロップダウンからアカウントを選択。

複数アカウント（例: GitLab.com + セルフホスト）に対応しています。

---

## アクション

### Pipeline Status

最新パイプラインのライブ状態（success / pending / running / failed / canceled）。**RUNNING** 中は実行検出時に `00:00:00` からタイマーが始まります。

| 操作 | 動作 |
|---|---|
| **短押し** | 状態に応じて: 更新（`success` / `pending` / idle / `canceled`）；パイプラインを開く（`running`）；失敗ジョブを開く（`failed`） |
| **長押し**（約 0.6 秒） | キャンセル（`pending` / `running`）；失敗ジョブを再試行（`failed`）；パイプラインを再試行（`canceled`） |

**設定**

| 項目 | 説明 |
|---|---|
| Account | GitLab アカウント |
| Project | パス `group/repo` または数値 ID |
| Branch / ref | 任意。最新パイプラインのフィルタ |
| Poll (sec) | 更新間隔（5–120、既定 15） |

---

### Open Pipeline

最新パイプライン番号（`#N`）を表示します。

| 操作 | 動作 |
|---|---|
| **クリック** | 最新パイプラインをブラウザで開く |

**設定:** Account、Project、Branch / ref（任意）。

---

### Run Pipeline

| 操作 | 動作 |
|---|---|
| **クリック** | 指定ブランチで新規パイプラインを作成（Branch が空ならプロジェクトの既定ブランチ） |

**設定:** Account、Project、Branch / ref（任意）。

---

### Retry Pipeline

| 操作 | 動作 |
|---|---|
| **クリック** | 最新の**失敗**パイプラインを再試行（ブランチでフィルタ可） |

**設定:** Account、Project、Branch / ref（任意）。

---

### Cancel Pipeline

| 操作 | 動作 |
|---|---|
| **クリック** | キャンセル可能な場合に最新パイプラインをキャンセル（`running`、`pending` など） |

**設定:** Account、Project、Branch / ref（任意）。

---

### Merge Requests

オープン中の MR 件数。ラベルは `MR`（すべて）または `MY MR`（自分に割り当て）。

| 操作 | 動作 |
|---|---|
| **クリック** | ブラウザで MR 一覧を開く（「Assigned to me」の場合はフィルタ済み） |

**設定**

| 項目 | 説明 |
|---|---|
| Account | GitLab アカウント |
| Project | プロジェクトのパスまたは ID |
| Count scope | **All open** = すべて；**Assigned to me** = トークンユーザーに割り当て |
| Poll (sec) | 更新間隔（最小 15 秒、既定 30） |

---

### Issues

オープン中の Issue 件数。ラベルは `ISSUES` または `MY ISSUES`。

| 操作 | 動作 |
|---|---|
| **クリック** | ブラウザで Issue 一覧を開く（必要に応じてフィルタ） |

**設定:** Merge Requests と同じ（Account、Project、Count scope、Poll）。

---

### Open Repository

| 操作 | 動作 |
|---|---|
| **クリック** | プロジェクト / リポジトリページを開く |

**設定:** Account、Project。キータイトルは短いリポジトリ名。

---

### Jobs Status

最新パイプラインのジョブ状態。例: `8/10 ✓`（状態により `✗` / `…`）。

| 操作 | 動作 |
|---|---|
| **クリック** | カウンタを更新 |

**設定:** Account、Project、Branch / ref（任意）、Poll (sec)。

---

### Failed Job

失敗したジョブ名を表示（`FAILED` + 名前。なければ `OK`）。

| 操作 | 動作 |
|---|---|
| **クリック** | 失敗ジョブのログをブラウザで開く |

**設定:** Account、Project、Branch / ref（任意）、Poll (sec)。

---

### Copy Branch Name

| 操作 | 動作 |
|---|---|
| **クリック** | 設定ブランチ、最新パイプラインのブランチ、または既定ブランチをクリップボードへコピー |

**設定:** Account、Project、Branch / ref（任意）。タイトルにブランチ名を表示。

---

### Copy Repository URL

| 操作 | 動作 |
|---|---|
| **クリック** | クローン URL（HTTP または SSH）をクリップボードへコピー |

**設定**

| 項目 | 説明 |
|---|---|
| Account | GitLab アカウント |
| Project | プロジェクトのパスまたは ID |
| URL kind | **HTTP** または **SSH** |

---

### Open Environments

| 操作 | 動作 |
|---|---|
| **クリック** | プロジェクトの `/-/environments` を開く |

**設定:** Account、Project。固定タイトル: `Env`。

---

### Open CI/CD

| 操作 | 動作 |
|---|---|
| **クリック** | プロジェクトの `/-/pipelines` を開く |

**設定:** Account、Project。固定タイトル: `CI/CD`。