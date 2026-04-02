## 🎯 Project Overview
A local-first, professional Kanban board designed for software engineers. It operates as a single-file application that uses the local file system as its primary database.

## 🛠 Technical Stack
- **Frontend:** Single-file HTML5, Vanilla JavaScript (ES6+), CSS3.
- **Storage:** `localStorage` for caching and the **File System Access API** for real-time synchronization with a `board.json` file.
- **Architecture:** Clean Code, separation of concerns within the script, and a focus on testability.

## 📋 Functional Requirements

### 1. Data & Sync
- **Single-File Truth:** All data (tasks, archived items) and UI configurations (columns, labels, priorities) live in one `board.json`.
- **Sync Handshake:** Visual indicator for sync status (✅/❌). Silent background saving on every change once linked.
- **Reset Function:** Ability to clear the local cache without affecting the JSON file.

### 2. Kanban Board Logic
- **Dynamic Columns:** Columns are rendered based on the `config` object in the JSON.
- **Drag & Drop:** - Full drag-and-drop support for moving cards between columns and reordering within columns.
    - **Visual Feedback:** A dedicated `drop-indicator` (line) must show the exact landing position during drag.
- **Search:** Real-time filtering of cards based on title.

### 3. Task Management
- **Task Creation:** Quick-add via a prompt or modal.
- **Subtasks (Checklist):** - Manageable via the task edit modal.
    - Progress visualization on the card (e.g., "📋 2/5").
- **Metadata:** Support for custom labels and priorities (defined in config) with color-coding.
- **Notes:** Markdown-ready textarea for implementation details and technical documentation.

### 4. Archive & Done Workflow
- **Done-to-Archive:** Tasks in the "Done" column feature a checkbox.
- **Check logic:**
    - **Checking** the box moves the task to the **Archive Section** at the bottom of the "Done" column.
    - **Unchecking** a task in the Archive restores it to the active "Done" list.
- **Purge:** Option to permanently delete all archived items.
- **Collapsible Archive:**
    - The Archive Section must be collapsible/expandable to save vertical space.
    - **Visual Indicator:** Use toggle icons (e.g., ▶/▼) to indicate the current state.
    - **Stateless Toggle:** The expansion state is UI-only and does not need to be persisted in the JSON.
    - **Containment:** When collapsed, all archived cards must be completely hidden from the DOM flow (display: none).

### 5. Daily Notes Feature
- **Daily Prep Widget:** A dedicated side-panel or modal for daily stand-up preparation.
- **Project Grouping:** Ability to generate a template that automatically groups current tasks by their assigned labels (Projects).
- **Drafting:** The daily note is persisted in the state/JSON to prevent data loss during the day.

### 6. UI/UX Requirements
- **Language:** UI, labels, placeholders, and technical comments must be in **English**.
- **Page Title:** The HTML `<title>` must be set to `Dev Kanban`.
- **Project Title:** The title in the header is editable; it updates the JSON and the browser tab title.
- **Editable Project Title:** The title in the header is editable; it updates the JSON and the browser tab title dynamically.
- - **Favicon:** Use a data-URI SVG icon (📋) within the meta tags.
- **Responsiveness:** Clean, developer-centric design (Dark Mode optimized) using CSS variables and system fonts.

## 💾 Expected JSON Structure
```json
{
  "config": {
    "projectTitle": "Project Name",
    "columns": [{"id": "todo", "title": "To Do"}],
    "labels": [{"id": "bug", "title": "Bug", "color": "#ff0000"}],
    "priorities": [{"id": "high", "title": "High", "color": "#ff0000"}]
  },
  "tasks": [
    {
      "id": "id-123",
      "title": "Fix Bug",
      "status": "todo",
      "label": "bug",
      "priority": "high",
      "subtasks": [{"text": "Investigate", "done": true}],
      "notes": "..."
    }
  ],
  "archived": [],
  "dailyDraft": ""
}
```
