# GitLab for Stream Deck

[Español](README.es.md) · [English](README.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [日本語](README.ja.md) · **한국어** · [简体中文](README.zh_CN.md) · [繁體中文](README.zh_TW.md)

GitLab.com 또는 셀프호스팅 파이프라인을 모니터링·제어하고, MR/이슈 개수를 표시하며, 프로젝트 화면을 열고 유용한 데이터를 복사하는 Stream Deck 플러그인입니다.

## 요구 사항

- Stream Deck 7.1+
- **api** 스코프 Personal Access Token

## 계정 (전역)

토큰은 플러그인 수준에 한 번만 저장되며 모든 액션에서 재사용됩니다.

1. 아무 액션에서 **Manage accounts…** 를 열거나 **Add accounts** 를 선택합니다.
2. **Name**, **Token**, **Domain**(선택, 셀프호스팅; 기본값 `https://gitlab.com`)을 입력합니다.
3. 각 키에서 **Account** 드롭다운으로 계정을 선택합니다.

여러 계정(예: GitLab.com + 셀프호스팅)을 사용할 수 있습니다.

---

## 액션

### Pipeline Status

최신 파이프라인 실시간 상태(success, pending, running, failed, canceled). **RUNNING** 중에는 실행이 감지되면 타이머가 `00:00:00`부터 시작합니다.

| 입력 | 동작 |
|---|---|
| **짧게** | 상태에 따라: 새로고침(`success` / `pending` / idle / `canceled`); 파이프라인 열기(`running`); 실패한 잡 열기(`failed`) |
| **길게** (~0.6초) | 취소(`pending` / `running`); 실패 잡 재시도(`failed`); 파이프라인 재시도(`canceled`) |

**설정**

| 필드 | 설명 |
|---|---|
| Account | GitLab 계정 |
| Project | 경로 `group/repo` 또는 숫자 ID |
| Branch / ref | 선택. 최신 파이프라인 필터 |
| Poll (sec) | 갱신 간격(5–120, 기본 15) |

---

### Open Pipeline

최신 파이프라인 번호(`#N`)를 표시합니다.

| 입력 | 동작 |
|---|---|
| **클릭** | 브라우저에서 최신 파이프라인 열기 |

**설정:** Account, Project, Branch / ref(선택).

---

### Run Pipeline

| 입력 | 동작 |
|---|---|
| **클릭** | 지정한 브랜치에 새 파이프라인 생성(Branch가 비어 있으면 프로젝트 기본 브랜치) |

**설정:** Account, Project, Branch / ref(선택).

---

### Retry Pipeline

| 입력 | 동작 |
|---|---|
| **클릭** | 최신 **실패** 파이프라인 재시도(브랜치로 필터 가능) |

**설정:** Account, Project, Branch / ref(선택).

---

### Cancel Pipeline

| 입력 | 동작 |
|---|---|
| **클릭** | 취소 가능한 경우 최신 파이프라인 취소(`running`, `pending` 등) |

**설정:** Account, Project, Branch / ref(선택).

---

### Merge Requests

열린 MR 개수. 라벨 `MR`(전체) 또는 `MY MR`(나에게 할당).

| 입력 | 동작 |
|---|---|
| **클릭** | 브라우저에서 MR 목록 열기(“Assigned to me”면 필터됨) |

**설정**

| 필드 | 설명 |
|---|---|
| Account | GitLab 계정 |
| Project | 프로젝트 경로 또는 ID |
| Count scope | **All open** = 전체 열림; **Assigned to me** = 토큰 사용자에게 할당 |
| Poll (sec) | 갱신 간격(최소 15초, 기본 30) |

---

### Issues

열린 이슈 개수. 라벨 `ISSUES` 또는 `MY ISSUES`.

| 입력 | 동작 |
|---|---|
| **클릭** | 브라우저에서 이슈 목록 열기(해당 시 필터) |

**설정:** Merge Requests와 동일(Account, Project, Count scope, Poll).

---

### Open Repository

| 입력 | 동작 |
|---|---|
| **클릭** | 프로젝트 / 저장소 페이지 열기 |

**설정:** Account, Project. 키 제목은 짧은 저장소 이름.

---

### Jobs Status

최신 파이프라인 잡 상태. 예: `8/10 ✓`(상태에 따라 `✗` / `…`).

| 입력 | 동작 |
|---|---|
| **클릭** | 카운터 새로고침 |

**설정:** Account, Project, Branch / ref(선택), Poll (sec).

---

### Failed Job

실패한 잡 이름 표시(`FAILED` + 이름, 없으면 `OK`).

| 입력 | 동작 |
|---|---|
| **클릭** | 실패한 잡 로그를 브라우저에서 열기 |

**설정:** Account, Project, Branch / ref(선택), Poll (sec).

---

### Copy Branch Name

| 입력 | 동작 |
|---|---|
| **클릭** | 설정 브랜치, 최신 파이프라인 브랜치 또는 기본 브랜치를 클립보드에 복사 |

**설정:** Account, Project, Branch / ref(선택). 제목에 브랜치 이름 표시.

---

### Copy Repository URL

| 입력 | 동작 |
|---|---|
| **클릭** | 클론 URL(HTTP 또는 SSH)을 클립보드에 복사 |

**설정**

| 필드 | 설명 |
|---|---|
| Account | GitLab 계정 |
| Project | 프로젝트 경로 또는 ID |
| URL kind | **HTTP** 또는 **SSH** |

---

### Open Environments

| 입력 | 동작 |
|---|---|
| **클릭** | 프로젝트 `/-/environments` 열기 |

**설정:** Account, Project. 고정 제목: `Env`.

---

### Open CI/CD

| 입력 | 동작 |
|---|---|
| **클릭** | 프로젝트 `/-/pipelines` 열기 |

**설정:** Account, Project. 고정 제목: `CI/CD`.

