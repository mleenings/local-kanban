# Local Development Kanban Board

A professional, offline-first Kanban board designed for software engineers. It prioritizes data sovereignty, flexible workflow mapping, and a seamless link to local technical documentation.

## 🚀 Purpose
This tool follows the **First Principles** of developer productivity:
1.  **Visualization:** Flexible mapping of any engineering pipeline via JSON.
2.  **Data Sovereignty:** All data, UI settings, and project metadata live in one human-readable file.
3.  **Context Persistence:** Seamless transition between high-level status and local file-system documentation.

---

## 📂 Project Structure

The board is designed to live directly within your project root or a dedicated workspace.

```text
/my-project-workspace
│
├── board.html             # The App (Single-file HTML/JS)
├── board.json             # THE TRUTH: Title, Config, Tasks, and Archive
│
├── /_template             # BLUEPRINT: Copy this for every new task
│   ├── notes.md           # Technical analysis & decisions
│   └── dod.md             # Local Definition of Done checklist
│
└── /tasks                 # Active deep-dive task data
    └── /TASK-ID-name      # Individual folders for documentation
```

---

## ⚙️ Configuration (board.json)

Die `board.json` steuert das gesamte Verhalten. Änderungen in der Datei werden beim nächsten Laden (oder nach dem Sync) sofort im UI reflektiert:

### Anpassbare Parameter im `config`-Objekt:
* **`projectTitle`**: Setzt den Namen im Header und im Browser-Tab (für Multitasking zwischen Projekten).
* **`columns`**: Definiere beliebig viele Spalten mit `id` und `title`.
* **`labels`**: Erstelle projektspezifische Badges mit `id`, `title` und Hex-`color`.
* **`priorities`**: Definiere dein eigenes Prioritätssystem (z. B. P0-P4) inklusive Farben.

### Beispiel-Schema:
```json
{
  "config": {
    "projectTitle": "Kunde Alpha - Service Migration",
    "columns": [
      { "id": "backlog", "title": "Backlog" },
      { "id": "todo", "title": "To Do" },
      { "id": "progress", "title": "In Arbeit" },
      { "id": "done", "title": "Erledigt" }
    ],
    "labels": [
      { "id": "infra", "title": "Infrastructure", "color": "#5aac44" }
    ],
    "priorities": [
      { "id": "high", "title": "Kritisch", "color": "#eb5a46" },
      { "id": "mid", "title": "Standard", "color": "#f2d600" }
    ]
  },
  "tasks": [],
  "archived": []
}
```

---

## 🛠 Setup & Workflow

1.  **Sync-Handshake:** Öffne `board.html` und verknüpfe deine `board.json` über den Button oben rechts. Dieser "Handshake" ist nach jedem Refresh der Seite einmalig nötig.
2.  **Edit Project Title:** Klicke direkt auf den Projekttitel im Header, um ihn zu ändern. Er wird sofort in der JSON gespeichert.
3.  **Task Documentation:**
    * Erstelle einen Task im Board.
    * Erstelle manuell einen Ordner in `/tasks/` mit der generierten Task-ID.
    * Nutze die Markdown-Templates aus `/_template` für die technische Dokumentation.
4.  **Auto-Save:** Jede Interaktion (Verschieben, Editieren, Archivieren) wird sofort und lautlos in die `board.json` geschrieben.

---

## ⚠️ Connectivity Note
Ein rotes **X** am Sync-Button bedeutet: **Read-Only**. Klicke den Button, um die Datei erneut zu verknüpfen und den automatischen Schreibzugriff zu aktivieren.

---

## ⚖️ License
MIT License - Open for engineering excellence.
