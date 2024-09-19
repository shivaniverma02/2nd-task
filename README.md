<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <input type="text" id="todo-input" placeholder="Add a new task...">
        <button id="add-btn">Add Task</button>
        <ul id="todo-list"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f7f7f7;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

input[type="text"] {
    width: 80%;
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
    border: 1px solid #ddd;
}

button {
    padding: 10px 20px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    background-color: #f9f9f9;
    margin: 5px 0;
    padding: 10px;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
}

li button {
    background-color: #dc3545;
    border: none;
    padding: 5px 10px;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

li button:hover {
    background-color: #c82333;
}
document.getElementById('add-btn').addEventListener('click', addTask);

function addTask() {
    let taskInput = document.getElementById('todo-input');
    let taskText = taskInput.value.trim();

    if (taskText === '') {
        alert('Please enter a task.');
        return;
    }

    let li = document.createElement('li');
    li.innerHTML = `
        ${taskText} 
        <button onclick="deleteTask(this)">Delete</button>
    `;
    
    document.getElementById('todo-list').appendChild(li);
    taskInput.value = '';
}

function deleteTask(button) {
    button.parentElement.remove();
}
