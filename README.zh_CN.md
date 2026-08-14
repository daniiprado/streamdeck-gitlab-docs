# GitLab for Stream Deck

[Español](README.es.md) · [English](README.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · **简体中文** · [繁體中文](README.zh_TW.md)

用于监控和控制 GitLab.com 或自托管实例流水线、显示 MR/Issue 计数、打开项目页面并复制常用数据的 Stream Deck 插件。

## 要求

- Stream Deck 7.1+
- 具有 **api** 权限的 Personal Access Token

## 账户（全局）

令牌在插件级别只保存一次，并在所有操作中复用：

1. 在任意操作中打开 **Manage accounts…** 或选择 **Add accounts**。
2. 填写 **Name**、**Token** 和 **Domain**（可选，自托管；默认 `https://gitlab.com`）。
3. 在每个按键上从 **Account** 下拉框选择账户。

可配置多个账户（例如 GitLab.com + 自托管）。

---

## 操作

### Pipeline Status

最新流水线的实时状态（success、pending、running、failed、canceled）。处于 **RUNNING** 时，检测到运行后计时器从 `00:00:00` 开始。

| 按键 | 行为 |
|---|---|
| **短按** | 按状态：刷新（`success` / `pending` / idle / `canceled`）；打开流水线（`running`）；打开失败的 job（`failed`） |
| **长按**（约 0.6 秒） | 取消（`pending` / `running`）；重试失败的 job（`failed`）；重试流水线（`canceled`） |

**配置**

| 字段 | 说明 |
|---|---|
| Account | GitLab 账户 |
| Project | 路径 `group/repo` 或数字 ID |
| Branch / ref | 可选；过滤最新流水线 |
| Poll (sec) | 刷新间隔（5–120；默认 15） |

---

### Open Pipeline

显示最新流水线编号（`#N`）。

| 按键 | 行为 |
|---|---|
| **点击** | 在浏览器中打开最新流水线 |

**配置：** Account、Project、Branch / ref（可选）。

---

### Run Pipeline

| 按键 | 行为 |
|---|---|
| **点击** | 在指定分支上创建新流水线（Branch 为空则使用项目默认分支） |

**配置：** Account、Project、Branch / ref（可选）。

---

### Retry Pipeline

| 按键 | 行为 |
|---|---|
| **点击** | 重试最近一次**失败**的流水线（可按分支过滤） |

**配置：** Account、Project、Branch / ref（可选）。

---

### Cancel Pipeline

| 按键 | 行为 |
|---|---|
| **点击** | 在可取消时取消最新流水线（`running`、`pending` 等） |

**配置：** Account、Project、Branch / ref（可选）。

---

### Merge Requests

打开的合并请求计数。标签为 `MR`（全部）或 `MY MR`（分配给你的）。

| 按键 | 行为 |
|---|---|
| **点击** | 在浏览器中打开 MR 列表（若为 “Assigned to me” 则带过滤） |

**配置**

| 字段 | 说明 |
|---|---|
| Account | GitLab 账户 |
| Project | 项目路径或 ID |
| Count scope | **All open** = 全部打开；**Assigned to me** = 分配给令牌用户 |
| Poll (sec) | 刷新间隔（最少 15 秒；默认 30） |

---

### Issues

打开的 Issue 计数。标签为 `ISSUES` 或 `MY ISSUES`。

| 按键 | 行为 |
|---|---|
| **点击** | 在浏览器中打开 Issue 列表（必要时带过滤） |

**配置：** 与 Merge Requests 相同（Account、Project、Count scope、Poll）。

---

### Open Repository

| 按键 | 行为 |
|---|---|
| **点击** | 打开项目 / 仓库页面 |

**配置：** Account、Project。按键标题显示简短仓库名。

---

### Jobs Status

最新流水线的 Job 状态，例如 `8/10 ✓`（或根据状态显示 `✗` / `…`）。

| 按键 | 行为 |
|---|---|
| **点击** | 刷新计数 |

**配置：** Account、Project、Branch / ref（可选）、Poll (sec)。

---

### Failed Job

显示失败的 Job 名称（`FAILED` + 名称；若无失败则为 `OK`）。

| 按键 | 行为 |
|---|---|
| **点击** | 在浏览器中打开失败 Job 的日志 |

**配置：** Account、Project、Branch / ref（可选）、Poll (sec)。

---

### Copy Branch Name

| 按键 | 行为 |
|---|---|
| **点击** | 将配置的分支、最新流水线分支或默认分支复制到剪贴板 |

**配置：** Account、Project、Branch / ref（可选）。标题显示分支名。

---

### Copy Repository URL

| 按键 | 行为 |
|---|---|
| **点击** | 将克隆 URL（HTTP 或 SSH）复制到剪贴板 |

**配置**

| 字段 | 说明 |
|---|---|
| Account | GitLab 账户 |
| Project | 项目路径或 ID |
| URL kind | **HTTP** 或 **SSH** |

---

### Open Environments

| 按键 | 行为 |
|---|---|
| **点击** | 打开项目的 `/-/environments` |

**配置：** Account、Project。固定标题：`Env`。

---

### Open CI/CD

| 按键 | 行为 |
|---|---|
| **点击** | 打开项目的 `/-/pipelines` |

**配置：** Account、Project。固定标题：`CI/CD`。

## 支持

☕ **请我喝杯咖啡**  
如果这个插件帮你节省了时间，可以在这里支持开发：  
https://paypal.me/danielpradom