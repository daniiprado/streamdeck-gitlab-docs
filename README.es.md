# GitLab for Stream Deck

**Español** · [English](README.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [简体中文](README.zh_CN.md) · [繁體中文](README.zh_TW.md)

Plugin de Stream Deck para monitorear y controlar pipelines de GitLab.com o instancias Self-Managed, ver contadores de MRs/issues, abrir secciones del proyecto y copiar datos útiles.

## Requisitos

- Stream Deck 7.1+
- Personal Access Token con scope **api**

## Cuentas (global)

Los tokens se guardan una sola vez a nivel de plugin y se reutilizan en todas las acciones:

1. En cualquier acción, abre **Manage accounts…** o elige **Add accounts**.
2. Completa **Name**, **Token** y **Domain** (opcional, self-hosted; por defecto `https://gitlab.com`).
3. En cada tecla, selecciona la cuenta en el desplegable **Account**.

Puedes tener varias cuentas (p. ej. GitLab.com + self-hosted).

---

## Acciones

### Pipeline Status

Estado en vivo del último pipeline (éxito, pending, running, failed, canceled). En **RUNNING** muestra un timer que arranca en `00:00:00` al detectar la ejecución.

| Pulsación | Comportamiento |
|---|---|
| **Corta** | Según estado: refrescar (`success` / `pending` / idle / `canceled`); abrir pipeline (`running`); abrir job fallido (`failed`) |
| **Larga** (~0,6 s) | Cancelar (`pending` / `running`); reintentar jobs fallidos (`failed`); reintentar pipeline (`canceled`) |

**Configuración**

| Campo | Descripción |
|---|---|
| Account | Cuenta GitLab |
| Project | Ruta `grupo/repo` o ID numérico |
| Branch / ref | Opcional; filtra el último pipeline |
| Poll (sec) | Intervalo de actualización (5–120; por defecto 15) |

---

### Open Pipeline

Muestra el número del último pipeline (`#N`).

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre el último pipeline en el navegador |

**Configuración:** Account, Project, Branch / ref (opcional).

---

### Run Pipeline

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Crea un nuevo pipeline en la rama indicada (si Branch está vacío, usa la rama por defecto del proyecto) |

**Configuración:** Account, Project, Branch / ref (opcional).

---

### Retry Pipeline

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Reintenta el último pipeline **fallido** (opcionalmente filtrado por rama) |

**Configuración:** Account, Project, Branch / ref (opcional).

---

### Cancel Pipeline

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Cancela el último pipeline si está en estado cancelable (`running`, `pending`, etc.) |

**Configuración:** Account, Project, Branch / ref (opcional).

---

### Merge Requests

Contador de merge requests abiertos. Etiqueta `MR` (todos) o `MY MR` (asignados a ti).

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre la lista de MRs en el navegador (filtrada si el alcance es “Assigned to me”) |

**Configuración**

| Campo | Descripción |
|---|---|
| Account | Cuenta GitLab |
| Project | Ruta o ID del proyecto |
| Count scope | **All open** = todos abiertos; **Assigned to me** = asignados al usuario del token |
| Poll (sec) | Intervalo de actualización (mín. 15 s; por defecto 30) |

---

### Issues

Contador de issues abiertos. Etiqueta `ISSUES` o `MY ISSUES`.

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre la lista de issues en el navegador (filtrada si aplica) |

**Configuración:** igual que Merge Requests (Account, Project, Count scope, Poll).

---

### Open Repository

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre la página del proyecto / repositorio |

**Configuración:** Account, Project. El título de la tecla muestra el nombre corto del repo.

---

### Jobs Status

Estado de jobs del último pipeline, p. ej. `8/10 ✓` (o `✗` / `…` según el estado).

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Refresca el contador |

**Configuración:** Account, Project, Branch / ref (opcional), Poll (sec).

---

### Failed Job

Muestra el nombre del job fallido (`FAILED` + nombre, o `OK` si no hay fallos).

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre el log del job fallido en el navegador |

**Configuración:** Account, Project, Branch / ref (opcional), Poll (sec).

---

### Copy Branch Name

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Copia al portapapeles la rama configurada, o la del último pipeline, o la rama por defecto |

**Configuración:** Account, Project, Branch / ref (opcional). El título muestra el nombre de la rama.

---

### Copy Repository URL

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Copia la URL de clonado (HTTP o SSH) al portapapeles |

**Configuración**

| Campo | Descripción |
|---|---|
| Account | Cuenta GitLab |
| Project | Ruta o ID del proyecto |
| URL kind | **HTTP** o **SSH** |

---

### Open Environments

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre `/-/environments` del proyecto |

**Configuración:** Account, Project. Título fijo: `Env`.

---

### Open CI/CD

| Pulsación | Comportamiento |
|---|---|
| **Clic** | Abre `/-/pipelines` del proyecto |

**Configuración:** Account, Project. Título fijo: `CI/CD`.

## Apoyo

☕ **Invítame a un café**  
Si este plugin te ahorra tiempo, puedes apoyar el desarrollo aquí:  
https://paypal.me/danielpradom