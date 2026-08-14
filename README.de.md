# GitLab for Stream Deck

[Español](README.es.md) · [English](README.md) · **Deutsch** · [Français](README.fr.md) · [日本語](README.ja.md) · [한국어](README.ko.md) · [简体中文](README.zh_CN.md) · [繁體中文](README.zh_TW.md)

Stream-Deck-Plugin zum Überwachen und Steuern von Pipelines auf GitLab.com oder Self-Managed-Instanzen, Anzeige von MR-/Issue-Zählern, Öffnen von Projektbereichen und Kopieren nützlicher Daten.

## Voraussetzungen

- Stream Deck 7.1+
- Personal Access Token mit Scope **api**

## Konten (global)

Tokens werden einmal auf Plugin-Ebene gespeichert und in allen Aktionen wiederverwendet:

1. In einer beliebigen Aktion **Manage accounts…** öffnen oder **Add accounts** wählen.
2. **Name**, **Token** und **Domain** ausfüllen (optional, self-hosted; Standard `https://gitlab.com`).
3. Auf jeder Taste das Konto im Dropdown **Account** auswählen.

Mehrere Konten sind möglich (z. B. GitLab.com + self-hosted).

---

## Aktionen

### Pipeline Status

Live-Status der neuesten Pipeline (success, pending, running, failed, canceled). Bei **RUNNING** startet ein Timer bei `00:00:00`, sobald der Lauf erkannt wird.

| Tastendruck | Verhalten |
|---|---|
| **Kurz** | Je nach Status: aktualisieren (`success` / `pending` / idle / `canceled`); Pipeline öffnen (`running`); fehlgeschlagenen Job öffnen (`failed`) |
| **Lang** (~0,6 s) | Abbrechen (`pending` / `running`); fehlgeschlagene Jobs erneut versuchen (`failed`); Pipeline erneut versuchen (`canceled`) |

**Einstellungen**

| Feld | Beschreibung |
|---|---|
| Account | GitLab-Konto |
| Project | Pfad `gruppe/repo` oder numerische ID |
| Branch / ref | Optional; filtert die neueste Pipeline |
| Poll (sec) | Aktualisierungsintervall (5–120; Standard 15) |

---

### Open Pipeline

Zeigt die Nummer der neuesten Pipeline (`#N`).

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet die neueste Pipeline im Browser |

**Einstellungen:** Account, Project, Branch / ref (optional).

---

### Run Pipeline

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Erstellt eine neue Pipeline auf dem angegebenen Branch (leer = Standardbranch des Projekts) |

**Einstellungen:** Account, Project, Branch / ref (optional).

---

### Retry Pipeline

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Startet die neueste **fehlgeschlagene** Pipeline erneut (optional nach Branch gefiltert) |

**Einstellungen:** Account, Project, Branch / ref (optional).

---

### Cancel Pipeline

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Bricht die neueste Pipeline ab, wenn sie abbrechbar ist (`running`, `pending`, usw.) |

**Einstellungen:** Account, Project, Branch / ref (optional).

---

### Merge Requests

Zähler offener Merge Requests. Label `MR` (alle) oder `MY MR` (dir zugewiesen).

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet die MR-Liste im Browser (gefiltert bei „Assigned to me“) |

**Einstellungen**

| Feld | Beschreibung |
|---|---|
| Account | GitLab-Konto |
| Project | Projektpfad oder ID |
| Count scope | **All open** = alle offenen; **Assigned to me** = dem Token-Benutzer zugewiesen |
| Poll (sec) | Aktualisierungsintervall (min. 15 s; Standard 30) |

---

### Issues

Zähler offener Issues. Label `ISSUES` oder `MY ISSUES`.

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet die Issue-Liste im Browser (ggf. gefiltert) |

**Einstellungen:** wie Merge Requests (Account, Project, Count scope, Poll).

---

### Open Repository

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet die Projekt-/Repository-Seite |

**Einstellungen:** Account, Project. Der Tastentitel zeigt den kurzen Repo-Namen.

---

### Jobs Status

Job-Status der neuesten Pipeline, z. B. `8/10 ✓` (oder `✗` / `…` je nach Status).

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Aktualisiert den Zähler |

**Einstellungen:** Account, Project, Branch / ref (optional), Poll (sec).

---

### Failed Job

Zeigt den Namen des fehlgeschlagenen Jobs (`FAILED` + Name, oder `OK` wenn keiner fehlgeschlagen ist).

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet das Log des fehlgeschlagenen Jobs im Browser |

**Einstellungen:** Account, Project, Branch / ref (optional), Poll (sec).

---

### Copy Branch Name

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Kopiert den konfigurierten Branch, den der neuesten Pipeline oder den Standardbranch in die Zwischenablage |

**Einstellungen:** Account, Project, Branch / ref (optional). Der Titel zeigt den Branchnamen.

---

### Copy Repository URL

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Kopiert die Clone-URL (HTTP oder SSH) in die Zwischenablage |

**Einstellungen**

| Feld | Beschreibung |
|---|---|
| Account | GitLab-Konto |
| Project | Projektpfad oder ID |
| URL kind | **HTTP** oder **SSH** |

---

### Open Environments

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet `/-/environments` des Projekts |

**Einstellungen:** Account, Project. Fester Titel: `Env`.

---

### Open CI/CD

| Tastendruck | Verhalten |
|---|---|
| **Klick** | Öffnet `/-/pipelines` des Projekts |

**Einstellungen:** Account, Project. Fester Titel: `CI/CD`.

## Unterstützung

☕ **Lad mich auf einen Kaffee ein**  
Wenn dir dieses Plugin Zeit spart, kannst du die Entwicklung hier unterstützen:  
https://paypal.me/danielpradom