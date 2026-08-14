# GitLab for Stream Deck

[Español](README.es.md) · [English](README.md) · [Deutsch](README.de.md) · **Français** · [日本語](README.ja.md) · [한국어](README.ko.md) · [简体中文](README.zh_CN.md) · [繁體中文](README.zh_TW.md)

Plugin Stream Deck pour surveiller et contrôler les pipelines GitLab.com ou self-managed, afficher les compteurs de MR/issues, ouvrir des sections du projet et copier des données utiles.

## Prérequis

- Stream Deck 7.1+
- Personal Access Token avec le scope **api**

## Comptes (global)

Les jetons sont enregistrés une seule fois au niveau du plugin et réutilisés dans toutes les actions :

1. Dans n’importe quelle action, ouvrez **Manage accounts…** ou choisissez **Add accounts**.
2. Renseignez **Name**, **Token** et **Domain** (optionnel, self-hosted ; défaut `https://gitlab.com`).
3. Sur chaque touche, sélectionnez le compte dans la liste **Account**.

Plusieurs comptes sont possibles (ex. GitLab.com + self-hosted).

---

## Actions

### Pipeline Status

État en direct du dernier pipeline (success, pending, running, failed, canceled). En **RUNNING**, un timer démarre à `00:00:00` à la détection de l’exécution.

| Appui | Comportement |
|---|---|
| **Court** | Selon l’état : actualiser (`success` / `pending` / idle / `canceled`) ; ouvrir le pipeline (`running`) ; ouvrir le job échoué (`failed`) |
| **Long** (~0,6 s) | Annuler (`pending` / `running`) ; relancer les jobs échoués (`failed`) ; relancer le pipeline (`canceled`) |

**Configuration**

| Champ | Description |
|---|---|
| Account | Compte GitLab |
| Project | Chemin `groupe/repo` ou ID numérique |
| Branch / ref | Optionnel ; filtre le dernier pipeline |
| Poll (sec) | Intervalle d’actualisation (5–120 ; défaut 15) |

---

### Open Pipeline

Affiche le numéro du dernier pipeline (`#N`).

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre le dernier pipeline dans le navigateur |

**Configuration :** Account, Project, Branch / ref (optionnel).

---

### Run Pipeline

| Appui | Comportement |
|---|---|
| **Clic** | Crée un nouveau pipeline sur la branche indiquée (vide = branche par défaut du projet) |

**Configuration :** Account, Project, Branch / ref (optionnel).

---

### Retry Pipeline

| Appui | Comportement |
|---|---|
| **Clic** | Relance le dernier pipeline **échoué** (éventuellement filtré par branche) |

**Configuration :** Account, Project, Branch / ref (optionnel).

---

### Cancel Pipeline

| Appui | Comportement |
|---|---|
| **Clic** | Annule le dernier pipeline s’il est annulable (`running`, `pending`, etc.) |

**Configuration :** Account, Project, Branch / ref (optionnel).

---

### Merge Requests

Compteur de merge requests ouvertes. Libellé `MR` (toutes) ou `MY MR` (qui vous sont assignées).

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre la liste des MR dans le navigateur (filtrée si « Assigned to me ») |

**Configuration**

| Champ | Description |
|---|---|
| Account | Compte GitLab |
| Project | Chemin ou ID du projet |
| Count scope | **All open** = toutes ouvertes ; **Assigned to me** = assignées à l’utilisateur du jeton |
| Poll (sec) | Intervalle d’actualisation (min. 15 s ; défaut 30) |

---

### Issues

Compteur d’issues ouvertes. Libellé `ISSUES` ou `MY ISSUES`.

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre la liste des issues dans le navigateur (filtrée le cas échéant) |

**Configuration :** identique à Merge Requests (Account, Project, Count scope, Poll).

---

### Open Repository

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre la page du projet / dépôt |

**Configuration :** Account, Project. Le titre de la touche affiche le nom court du dépôt.

---

### Jobs Status

État des jobs du dernier pipeline, ex. `8/10 ✓` (ou `✗` / `…` selon l’état).

| Appui | Comportement |
|---|---|
| **Clic** | Actualise le compteur |

**Configuration :** Account, Project, Branch / ref (optionnel), Poll (sec).

---

### Failed Job

Affiche le nom du job échoué (`FAILED` + nom, ou `OK` s’il n’y en a pas).

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre le log du job échoué dans le navigateur |

**Configuration :** Account, Project, Branch / ref (optionnel), Poll (sec).

---

### Copy Branch Name

| Appui | Comportement |
|---|---|
| **Clic** | Copie dans le presse-papiers la branche configurée, celle du dernier pipeline, ou la branche par défaut |

**Configuration :** Account, Project, Branch / ref (optionnel). Le titre affiche le nom de la branche.

---

### Copy Repository URL

| Appui | Comportement |
|---|---|
| **Clic** | Copie l’URL de clone (HTTP ou SSH) dans le presse-papiers |

**Configuration**

| Champ | Description |
|---|---|
| Account | Compte GitLab |
| Project | Chemin ou ID du projet |
| URL kind | **HTTP** ou **SSH** |

---

### Open Environments

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre `/-/environments` du projet |

**Configuration :** Account, Project. Titre fixe : `Env`.

---

### Open CI/CD

| Appui | Comportement |
|---|---|
| **Clic** | Ouvre `/-/pipelines` du projet |

**Configuration :** Account, Project. Titre fixe : `CI/CD`.

## Soutien

☕ **Offre-moi un café**  
Si ce plugin te fait gagner du temps, tu peux soutenir le développement ici :  
https://paypal.me/danielpradom