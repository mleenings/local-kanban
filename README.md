# Dev-Context-Board

A professional, offline-first Kanban board designed for software engineers who value deep task context and data sovereignty. This tool bridges the gap between visual high-level planning and low-level technical documentation.

## 🚀 Purpose
This system allows you to manage tasks without any external dependencies. It follows the **First Principles** of developer productivity:
1. **Visualization:** High-level overview of your current sprint/workload.
2. **Context Persistence:** Each card acts as a gateway to your local file-system notes.
3. **Local-First:** No accounts, no tracking, no cloud. Your data belongs to you.

---

## 📂 Recommended Project Structure

For maximum efficiency, use the board in combination with a structured file system:

```text
/my-project-root
│
├── board.html               # Visual planning tool (Single-file HTML/JS)
├── README.md                # This documentation
│
└── /tasks                   # Deep-dive task data
    ├── /TASK-ID-short-name  # Create manually for complex tasks
    │   ├── notes.md         # Technical analysis & decisions
    │   ├── error.log        # Raw system logs
    │   └── screenshot.png   # UI bugs or design drafts
    │
    └── /archive             # Move your finished task folders here
```

---

## ✨ Features

* **Single-File App:** Works offline in any modern browser without installation.
* **Rich Task Details:** Supports multiline notes and interactive subtask checklists within the UI.
* **Smart Done/Archive Workflow:** * Checking a task in the **Done** column automatically moves it to the collapsible Archive.
    * Unchecking a task in the **Archive** restores it to the active Done list.
* **Data Portability:** Integrated **Export & Import** functions to save your state as a `.json` file.
* **Developer UX:** Drag-and-drop movement and right-click to delete.

---

## 🛠 Usage Instructions

1. **Open:** Double-click `board.html`.
2. **Add:** Click `+` in any column to create a new task.
3. **Detail:** Click a card to open the modal for notes and checklists.
4. **Move:** Drag cards between columns to update status.
5. **Archive:** When a task is in the **Done** column, click the checkbox to move it into the Archive.
6. **Restore:** Open the Archive section at the bottom of the "Done" column and uncheck a task to bring it back.
7. **Backup:** Use the **Export Backup** button regularly to save your state as a file.

---

## ⚙️ Customization

Edit the `board.html` file in your favorite text editor to adapt the board:

### Change Columns
Modify the `COLUMNS` array in the `<script>` section:
```javascript
const COLUMNS = [
    { id: 'todo', title: 'To Do' },
    { id: 'doing', title: 'In Progress' },
    { id: 'done', title: 'Done' }
];
```

### Style UI
Adjust CSS variables in the `<style>` block:
```css
:root { 
    --bg: #0079bf; /* Background color */
    --accent: #0052cc; /* Button/Link color */
}
```

---

## ⚠️ Data & Persistence

* **Browser Storage:** Data is stored in `localStorage`. It persists through browser restarts.
* **Warning:** Clearing your browser's site data/cache will delete the board state.
* **Security:** Always use the **Export** button to create a JSON backup of your board, especially before switching browsers or clearing history.

---

## ⚖️ License

This project is licensed under the **MIT License**.
```
