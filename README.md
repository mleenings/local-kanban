# Local Kanban Board

A professional, offline-first Kanban board designed for software engineers who value deep task context and data sovereignty. This tool bridges the gap between visual high-level planning and low-level technical documentation.

## 🚀 Purpose
This system allows you to manage tasks without any external dependencies. It follows the **First Principles** of developer productivity:
1. **Visualization:** High-level overview of your current workflow.
2. **Context Persistence:** Each card acts as a gateway to your local file-system notes.
3. **Quality Gates:** Integrated checklists and a local "Definition of Done" (DoD) ensure high standards.

---

## 📂 Project Structure (Recommended)

Similar to **VS Code Portable**, this tool is designed to live directly within your project root or a dedicated workspace folder.

```text
/my-kanban-workspace
│
├── board.html               # The App (Single-file HTML/JS)
├── data.json                # AUTOMATIC: Your database (Sync Target)
├── README.md                # This documentation
│
├── /_template               # BLUEPRINT: Copy this for every new task
│   ├── notes.md             # Technical analysis & decisions
│   └── dod.md               # Local DoD checklist
│
└── /tasks                   # Active deep-dive task data
    └── /TASK-ID-name        # Folders for complex documentation
```

---

## ⚙️ Data Persistence & Auto-Sync

This version utilizes the modern **File System Access API**. It behaves like a native desktop application within your browser environment.

### 1. Initial Setup
* Create an empty file named `data.json` in your project folder (or use an existing export file).
* Open `board.html` in a modern browser (Chrome or Edge recommended).
* Click the **"🔗 Start Auto-Sync with data.json"** button at the top.
* Select your `data.json` file in the file picker.

### 2. The "Portable App" Workflow
* **The Handshake:** Due to browser security restrictions, the file permission is revoked when the tab is closed. Make it a habit to click the **Sync** button once every time you open the board.
* **Invisible Execution:** Once the connection is established, **every action** (moving cards, editing notes, deleting tasks) is immediately and silently written to your `data.json`.
* **Redundancy:** The board simultaneously updates the browser's `localStorage` as a secondary safety net.

---

## 🛠 Workflow Logic

The board uses a **Lean 6-Column Pipeline** to maintain strict quality gates:

1. **Backlog:** Future ideas and unprioritized tasks.
2. **To Do:** Tasks committed for the current session or sprint.
3. **In Progress:** Active development. Follow the local `DoD.md` templates here.
4. **To Verify:** Development is finished. Awaiting final local review.
5. **Dev-Env Test:** Verified in a live-like integration environment.
6. **Done:** Task is complete and ready for archival.

---

## ✨ Features

* **Zero-Install Desktop Feel:** No Node.js, Python, or database installation required.
* **True Auto-Save:** Behaves like local software once the initial file handshake is complete.
* **Smart Archive:** Completed tasks are moved to a collapsible UI archive but remain persisted in the JSON file.
* **Developer UX:** Lightweight, drag-and-drop enabled, and designed for speed.

---

## ⚠️ Important Note on Persistence

The browser "forgets" the file handle upon closing the tab for security reasons. 
**Best Practice:** Always check the status indicator in the header. If it says **"Offline"**, click the Sync button to ensure your `data.json` stays updated with your latest changes.

---

## ⚖️ License
This project is licensed under the **MIT License**.
