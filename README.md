# GitLab for Stream Deck

**English** · [Español](README.es.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [简体中文](README.zh_CN.md) · [繁體中文](README.zh_TW.md)

Stream Deck plugin to monitor and control GitLab.com or self-managed pipelines, show MR/issue counts, open project sections, and copy useful data.

## Requirements

- Stream Deck 7.1+
- Personal Access Token with **api** scope

## Accounts (global)

Tokens are stored once at the plugin level and reused across all actions:

1. On any action, open **Manage accounts…** or choose **Add accounts**.
2. Fill in **Name**, **Token**, and **Domain** (optional, self-hosted; default `https://gitlab.com`).
3. On each key, select the account from the **Account** dropdown.

You can keep several accounts (e.g. GitLab.com + self-hosted).

---

## Actions

### Pipeline Status

Live status of the latest pipeline (success, pending, running, failed, canceled). While **RUNNING**, a timer starts at `00:00:00` when the run is detected.

| Press | Behavior |
|---|---|
| **Short** | By state: refresh (`success` / `pending` / idle / `canceled`); open pipeline (`running`); open failed job (`failed`) |
| **Long** (~0.6 s) | Cancel (`pending` / `running`); retry failed jobs (`failed`); retry pipeline (`canceled`) |

**Settings**

| Field | Description |
|---|---|
| Account | GitLab account |
| Project | Path `group/repo` or numeric ID |
| Branch / ref | Optional; filters the latest pipeline |
| Poll (sec) | Refresh interval (5–120; default 15) |

---

### Open Pipeline

Shows the latest pipeline number (`#N`).

| Press | Behavior |
|---|---|
| **Click** | Opens the latest pipeline in the browser |

**Settings:** Account, Project, Branch / ref (optional).

---

### Run Pipeline

| Press | Behavior |
|---|---|
| **Click** | Creates a new pipeline on the given branch (if Branch is empty, uses the project default branch) |

**Settings:** Account, Project, Branch / ref (optional).

---

### Retry Pipeline

| Press | Behavior |
|---|---|
| **Click** | Retries the latest **failed** pipeline (optionally filtered by branch) |

**Settings:** Account, Project, Branch / ref (optional).

---

### Cancel Pipeline

| Press | Behavior |
|---|---|
| **Click** | Cancels the latest pipeline if it is cancelable (`running`, `pending`, etc.) |

**Settings:** Account, Project, Branch / ref (optional).

---

### Merge Requests

Open merge request counter. Label `MR` (all) or `MY MR` (assigned to you).

| Press | Behavior |
|---|---|
| **Click** | Opens the MR list in the browser (filtered when scope is “Assigned to me”) |

**Settings**

| Field | Description |
|---|---|
| Account | GitLab account |
| Project | Project path or ID |
| Count scope | **All open** = every open MR; **Assigned to me** = assigned to the token user |
| Poll (sec) | Refresh interval (min. 15 s; default 30) |

---

### Issues

Open issues counter. Label `ISSUES` or `MY ISSUES`.

| Press | Behavior |
|---|---|
| **Click** | Opens the issues list in the browser (filtered when applicable) |

**Settings:** same as Merge Requests (Account, Project, Count scope, Poll).

---

### Open Repository

| Press | Behavior |
|---|---|
| **Click** | Opens the project / repository page |

**Settings:** Account, Project. The key title shows the short repo name.

---

### Jobs Status

Job status for the latest pipeline, e.g. `8/10 ✓` (or `✗` / `…` depending on state).

| Press | Behavior |
|---|---|
| **Click** | Refreshes the counter |

**Settings:** Account, Project, Branch / ref (optional), Poll (sec).

---

### Failed Job

Shows the failed job name (`FAILED` + name, or `OK` if none failed).

| Press | Behavior |
|---|---|
| **Click** | Opens the failed job log in the browser |

**Settings:** Account, Project, Branch / ref (optional), Poll (sec).

---

### Copy Branch Name

| Press | Behavior |
|---|---|
| **Click** | Copies to the clipboard the configured branch, or the latest pipeline branch, or the default branch |

**Settings:** Account, Project, Branch / ref (optional). The title shows the branch name.

---

### Copy Repository URL

| Press | Behavior |
|---|---|
| **Click** | Copies the clone URL (HTTP or SSH) to the clipboard |

**Settings**

| Field | Description |
|---|---|
| Account | GitLab account |
| Project | Project path or ID |
| URL kind | **HTTP** or **SSH** |

---

### Open Environments

| Press | Behavior |
|---|---|
| **Click** | Opens the project `/-/environments` page |

**Settings:** Account, Project. Fixed title: `Env`.

---

### Open CI/CD

| Press | Behavior |
|---|---|
| **Click** | Opens the project `/-/pipelines` page |

**Settings:** Account, Project. Fixed title: `CI/CD`.
