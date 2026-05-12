# Ex03 To-Do List using JavaScript
## Date: 12.05.2026

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
### Developed BY: HARINI S
### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>To-Do App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="container">
    <h1>My Tasks <span id="cnt"></span></h1>

    <div class="add-row">
      <input type="text" id="inp" placeholder="Add a new task…" maxlength="120" />
      <button id="addBtn">+ Add</button>
    </div>

    <div class="filters">
      <button class="f-btn active" data-f="all">All</button>
      <button class="f-btn" data-f="active">Active</button>
      <button class="f-btn" data-f="done">Done</button>
    </div>

    <ul id="list"></ul>
    <p id="empty" class="empty" style="display:none">Nothing here yet.</p>
    <button id="clearBtn" class="clear-btn" style="display:none">Clear completed</button>
  </div>

  <script src="script.js"></script>
</body>
</html>
```
### style.css
```
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Segoe UI', sans-serif;
  background: #f4f4f5;
  min-height: 100vh;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding: 48px 16px;
}

.container {
  background: #ffffff;
  border-radius: 12px;
  border: 1px solid #e4e4e7;
  padding: 32px;
  width: 100%;
  max-width: 500px;
}

h1 {
  font-size: 22px;
  font-weight: 600;
  color: #18181b;
  margin-bottom: 24px;
  display: flex;
  align-items: baseline;
  gap: 10px;
}

h1 #cnt {
  font-size: 14px;
  font-weight: 400;
  color: #71717a;
}

.add-row {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

.add-row input {
  flex: 1;
  border: 1px solid #d4d4d8;
  border-radius: 8px;
  padding: 10px 14px;
  font-size: 15px;
  color: #18181b;
  outline: none;
  transition: border-color 0.15s;
}

.add-row input:focus {
  border-color: #6366f1;
}

.add-row input::placeholder {
  color: #a1a1aa;
}

.add-row button {
  background: #6366f1;
  color: #ffffff;
  border: none;
  border-radius: 8px;
  padding: 10px 18px;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.15s;
}

.add-row button:hover {
  background: #4f46e5;
}

.filters {
  display: flex;
  gap: 6px;
  margin-bottom: 20px;
}

.f-btn {
  font-size: 13px;
  padding: 5px 14px;
  border-radius: 999px;
  border: 1px solid #d4d4d8;
  background: transparent;
  color: #71717a;
  cursor: pointer;
  transition: all 0.12s;
}

.f-btn:hover {
  background: #f4f4f5;
  color: #18181b;
}

.f-btn.active {
  background: #18181b;
  border-color: #18181b;
  color: #ffffff;
}

#list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.task {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 11px 14px;
  border: 1px solid #e4e4e7;
  border-radius: 8px;
  background: #fafafa;
  animation: pop 0.15s ease;
}

@keyframes pop {
  from { opacity: 0; transform: translateY(-4px); }
  to   { opacity: 1; transform: none; }
}

.task:hover {
  border-color: #d4d4d8;
}

.task-cb {
  width: 18px;
  height: 18px;
  border: 1.5px solid #d4d4d8;
  border-radius: 4px;
  flex-shrink: 0;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.12s, border-color 0.12s;
}

.task-cb.done {
  background: #22c55e;
  border-color: #22c55e;
}

.task-cb.done::after {
  content: '';
  display: block;
  width: 5px;
  height: 9px;
  border: 2px solid #ffffff;
  border-top: none;
  border-left: none;
  transform: rotate(45deg) translateY(-1px);
}

.task-text {
  flex: 1;
  font-size: 15px;
  color: #18181b;
  word-break: break-word;
}

.task-text.done {
  color: #a1a1aa;
  text-decoration: line-through;
}

.task-del {
  background: none;
  border: none;
  font-size: 18px;
  color: #a1a1aa;
  cursor: pointer;
  padding: 0 2px;
  line-height: 1;
  opacity: 0;
  transition: opacity 0.12s, color 0.12s;
}

.task:hover .task-del {
  opacity: 1;
}

.task-del:hover {
  color: #ef4444;
}

.empty {
  text-align: center;
  color: #a1a1aa;
  font-size: 14px;
  padding: 32px 0;
}

.clear-btn {
  margin-top: 16px;
  font-size: 13px;
  background: none;
  border: 1px solid #e4e4e7;
  border-radius: 8px;
  color: #71717a;
  padding: 7px 14px;
  cursor: pointer;
  transition: color 0.12s, border-color 0.12s;
}

.clear-btn:hover {
  color: #ef4444;
  border-color: #ef4444;
}
```
### script.js
```
let tasks  = JSON.parse(localStorage.getItem('todo_tasks') || '[]');
let filter = 'all';

const inp      = document.getElementById('inp');
const addBtn   = document.getElementById('addBtn');
const list     = document.getElementById('list');
const cntEl    = document.getElementById('cnt');
const emptyEl  = document.getElementById('empty');
const clearBtn = document.getElementById('clearBtn');

function save() {
  localStorage.setItem('todo_tasks', JSON.stringify(tasks));
}

function render() {
  const visible = tasks.filter(t => {
    if (filter === 'active') return !t.done;
    if (filter === 'done')   return  t.done;
    return true;
  });

  list.innerHTML = '';

  visible.forEach(t => {
    const li = document.createElement('li');
    li.className = 'task';
    li.innerHTML = `
      <div class="task-cb ${t.done ? 'done' : ''}" data-id="${t.id}"></div>
      <span class="task-text ${t.done ? 'done' : ''}">${escHtml(t.text)}</span>
      <button class="task-del" data-id="${t.id}" title="Delete">&#x2715;</button>
    `;
    list.appendChild(li);
  });

  const remaining = tasks.filter(t => !t.done).length;
  cntEl.textContent      = remaining + ' left';
  emptyEl.style.display  = visible.length === 0 ? 'block' : 'none';
  clearBtn.style.display = tasks.some(t => t.done) ? 'inline-block' : 'none';
}

function addTask() {
  const text = inp.value.trim();
  if (!text) return inp.focus();
  tasks.unshift({ id: Date.now(), text, done: false });
  inp.value = '';
  save();
  render();
}

addBtn.addEventListener('click', addTask);
inp.addEventListener('keydown', e => { if (e.key === 'Enter') addTask(); });

list.addEventListener('click', e => {
  const cb  = e.target.closest('.task-cb');
  const del = e.target.closest('.task-del');

  if (cb) {
    const id = Number(cb.dataset.id);
    tasks = tasks.map(t => t.id === id ? { ...t, done: !t.done } : t);
    save();
    render();
  }

  if (del) {
    const id = Number(del.dataset.id);
    tasks = tasks.filter(t => t.id !== id);
    save();
    render();
  }
});

document.querySelectorAll('.f-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    filter = btn.dataset.f;
    document.querySelectorAll('.f-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    render();
  });
});

clearBtn.addEventListener('click', () => {
  tasks = tasks.filter(t => !t.done);
  save();
  render();
});

function escHtml(str) {
  return str
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;')
    .replace(/"/g, '&quot;');
}

render();
```

## OUTPUT
<img width="630" height="386" alt="Screenshot 2026-05-12 114639" src="https://github.com/user-attachments/assets/54bbd817-49cb-4403-ae87-a9de4f42b490" />
<img width="1077" height="643" alt="image" src="https://github.com/user-attachments/assets/5d4031e5-434d-4b4b-bc4c-cea67cbdbc5f" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
