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
│   └── dod.md               # Local "Definition of Done" checklist
│
└── /tasks                   # Active deep-dive task data
    ├── /TASK-ID-name        # EXAMPLE: Concrete task folder
    │   ├── meta.md          # Filled with specific Jira links, PO contact, etc.
    │   ├── notes.md         # Technical implementation details of the fix
    │   ├── dod.md           # Checked checklist for this specific task
    │   ├── error.log        # (Optional) Attached raw log data
    │   ├── screenshot.png   # (Optional) Visual proof of the resolved bug 
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

The board is designed to be easily configurable via the constant arrays at the top of the `<script>` section in the HTML file.

### 1. Label System (Optional)
The `LABELS` array allows you to define projects or categories with specific colors. If this array is empty (`[]`), all label-related UI elements will be hidden automatically.

```javascript
const LABELS = [
    { id: 'alpha', title: 'Alpha-Project', color: '#0052cc' },
    { id: 'beta', title: 'Beta-Service', color: '#eb5a46' }
];
```

* **id**: Unique identifier stored within the task data.
* **title**: Display name shown on cards and in the selection menu.
* **color**: CSS color (Hex, RGB, or Name) for the badge background.

### 2. Board Columns
You can modify the `COLUMNS` array to match your specific workflow (e.g., adding a "Ready for Release" stage).

```javascript
const COLUMNS = [
    { id: 'backlog', title: 'Backlog' },
    // ... add or remove stages here
    { id: 'done', title: 'Done' }
];
```

---

## 🛠 Technical Details

- **Data Persistence**: Uses `localStorage` (Key: `kanban_v6`).
- **Data Model**:
  - `tasks`: Active tasks currently on the board.
  - `archived`: Tasks moved to the archive.
  - `archiveOpen`: Persistent UI state of the archive toggle.
- **Label Mapping**: Tasks store only the label `id`. Visual properties (color/title) are mapped at runtime to ensure consistency across the application.

---

## ⚠️ Data & Persistence

* **Storage:** Data is stored in your browser's `localStorage`.
* **Risk:** Clearing browser cache/site data **will wipe the board**.
* **Best Practice:** 1. Use the **Export** button daily to save a JSON backup.
    2. Since your `/tasks` folders are on your disk, keep the root folder under **Git version control** for full redundancy.

---

## ⚖️ License

This project is licensed under the **MIT License**.
