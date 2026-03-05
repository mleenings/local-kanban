# Local Kanban Board

A professional, offline-first Kanban board designed for software engineers who value deep task context and data sovereignty. This tool bridges the gap between visual high-level planning and low-level technical documentation.

## 🚀 Purpose
This system allows you to manage tasks without any external dependencies. It follows the **First Principles** of developer productivity:
1. **Visualization:** High-level overview of your current workflow.
2. **Context Persistence:** Each card acts as a gateway to your local file-system notes.
3. **Quality Gates:** Integrated checklists and a local "Definition of Done" (DoD) ensure high standards before verification.

---

## 📂 Project Structure

For maximum efficiency, use the board in combination with a structured file system:

```text
/my-project-root
│
├── board.html               # Visual planning tool (Single-file HTML/JS)
├── README.md                # This documentation
│
├── /_template               # BLUEPRINT: Copy this for every new task
│   ├── notes.md             # Technical analysis, decisions & research
│   └── DoD.md               # Local "Definition of Done" checklist
│
└── /tasks                   # Active deep-dive task data
    ├── /TASK-ID-name        # Example: TASK-101-auth-fix
    └── /archive             # Move finished task FOLDERS here manually
```

---

## 🛠 Workflow Logic

This board uses a **Lean 6-Column Pipeline** to keep the interface clean while maintaining strict quality gates:

1. **Backlog:** Future ideas and unprioritized tasks.
2. **To Do:** Tasks committed for the current session/sprint.
3. **In Progress:** Active development. **Requirement:** Follow the local `DoD.md` here.
4. **To Verify:** Local development is finished. Card stays here for a "fresh eyes" review or final local double-check.
5. **Dev-Env Test:** Task is deployed to the dev/integration environment and awaits final verification in a live-like setting.
6. **Done:** Task is complete.

---

## ✨ Features

* **Single-File App:** Works offline in any modern browser without installation.
* **Template-Driven:** Encourages a consistent documentation style via the `/_template` folder.
* **Smart Archive:** * Checking a task in the **Done** column moves it to the collapsible UI Archive.
    * Unchecking a task in the **Archive** restores it to the active Done list.
* **Data Portability:** Integrated **Export & Import** functions to save your state as a `.json` file.
* **Developer UX:** Drag-and-drop movement and right-click to delete.

---

## ⚙️ Customization

Edit the `board.html` file to adapt the board. Current optimized setup:

```javascript
const COLUMNS = [
    { id: 'backlog', title: 'Backlog' },
    { id: 'todo', title: 'To Do' },
    { id: 'progress', title: 'In Progress' },
    { id: 'verify', title: 'To Verify' },
    { id: 'test_dev', title: 'Dev-Env Test' },
    { id: 'done', title: 'Done' }
];
```

---

## ⚠️ Data & Persistence

* **Storage:** Data is stored in your browser's `localStorage`.
* **Risk:** Clearing browser cache/site data **will wipe the board**.
* **Best Practice:** 1. Use the **Export** button daily to save a JSON backup.
    2. Since your `/tasks` folders are on your disk, keep the root folder under **Git version control** for full redundancy.

---

## ⚖️ License

This project is licensed under the **MIT License**.
