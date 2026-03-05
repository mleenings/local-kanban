# Personal Dev-Kanban & Task Management

A lightweight, offline-first task tracking system designed for software engineers. It combines a visual Kanban board with a structured, file-based documentation approach.

## 🚀 Purpose
This system allows you to manage tasks without an internet connection or any external dependencies. It follows the **First Principles** of task management:
1. **Visualization:** Immediate overview of the workflow (Kanban).
2. **Context Retention:** Dedicated storage for logs, screenshots, and deep-dive notes per task.
3. **Data Sovereignty:** Everything is stored locally in your browser's `localStorage` and on your file system.

---

## 📂 Project Structure

The project is structured to keep your workspace clean while providing deep context for every ticket:

```text
/my-project-root
│
├── board.html               # Visual planning tool (Single-file HTML/JS)
├── README.md                # Project documentation
│
└── /tasks                   # All task-related data
    ├── /TASK-ID-short-title # One folder per task (created manually)
    │   ├── notes.md         # Analysis, todos, and architectural decisions
    │   ├── error.log        # Raw system outputs or logs
    │   └── screenshot.png   # Visual evidence or UI drafts
    │
    └── /archive             # Move finished task folders here
```

---

## ✨ Features

* **Single-Page Kanban:** No installation, no server, works in any modern browser.
* **Dynamic Column Configuration:** Easily adapt the workflow to your needs.
* **Deep Task Details:** Support for multiline notes and interactive subtask checklists.
* **Smart Archiving:** Move finished tasks to a collapsible archive inside the "Done" column; includes a "Restore" function to move them back if needed.
* **Developer Workflow:** Designed for right-click deletion and drag-and-drop movement.
* **Persistent Storage:** Uses `localStorage` to keep your data between browser restarts.

---

## ⚙️ Customization

You can easily customize the board by editing the `board.html` file in a text editor.

### Modifying Columns
To change the workflow (e.g., adding a "Testing" or "Review" column), locate the `COLUMNS` array in the `<script>` section:

```javascript
const COLUMNS = [
    { id: 'todo', title: 'To Do' },
    { id: 'doing', title: 'In Progress' },
    { id: 'review', title: 'Code Review' }, // Added new column
    { id: 'done', title: 'Done' }
];
```

### Visual Styling
The look and feel (colors, widths, fonts) can be adjusted in the `<style>` block at the top of the file using the CSS variables:

```css
:root { 
    --bg: #0079bf; /* Change background color */
    --col: #ebedf0; 
    --card: #fff; 
}
```

---

## 🛠 Usage Instructions

1. **Open the Board:** Double-click `board.html`.
2. **Create Tasks:** Click the `+` button in any column.
3. **Manage Details:** Click a card to open the modal for notes and subtasks.
4. **Move Tasks:** Drag and drop cards between columns.
5. **Archive:** In the **Done** column, click the checkbox on a card to move it to the local archive.
6. **Restore:** Open the archive at the bottom of the "Done" column and uncheck a task to bring it back.
7. **Delete:** Right-click any card to delete it permanently.

---

## ⚠️ Important Note on Data
Since this tool runs entirely on the client side, data is stored in your **Browser's Local Storage**. 
* **Persistence:** Data survives browser restarts.
* **Data Loss:** Clearing your browser cache/site data will delete your board state. 
* **Backup:** It is recommended to keep your `/tasks` folder synced via Git or another local backup solution.
```
