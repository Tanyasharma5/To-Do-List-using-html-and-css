# To-Do-List-using-html-and-css
This project is an interactive and visually appealing to-do list web application. Designed with modern aesthetics and functionality, it allows users to efficiently manage their tasks with ease. The application includes features to add, mark as completed, edit, and delete tasks.   
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Enhanced To-Do List</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400&display=swap');

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #4A90E2 0%, #0033A0 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            color: #2c3e50;
        }
        .container {
            background-color: #ffffff;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            width: 450px;
            max-width: 100%;
        }
        h2 {
            text-align: center;
            color: #2c3e50;
            margin-bottom: 30px;
            font-size: 28px;
            font-family: 'Montserrat', sans-serif;
            letter-spacing: 1px;
            border-bottom: 3px solid #1abc9c;
            padding-bottom: 10px;
        }
        .task-input {
            display: flex;
            margin-bottom: 25px;
        }
        .task-input input {
            flex: 1;
            padding: 15px;
            border: 1px solid #bdc3c7;
            border-radius: 8px 0 0 8px;
            font-size: 16px;
            color: #2c3e50;
            background-color: #ecf0f1;
        }
        .task-input button {
            padding: 15px;
            border: none;
            background-color: #1abc9c;
            color: white;
            border-radius: 0 8px 8px 0;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        .task-input button:hover {
            background-color: #16a085;
        }
        .task-list {
            list-style-type: none;
            padding: 0;
        }
        .task-list li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border: 1px solid #bdc3c7;
            border-radius: 8px;
            margin-bottom: 15px;
            background-color: #f9f9f9;
            transition: background-color 0.3s;
        }
        .task-list li:hover {
            background-color: #ecf0f1;
        }
        .task-list li.completed span {
            text-decoration: line-through;
            color: #7f8c8d;
        }
        .task-list button {
            border: none;
            background: none;
            cursor: pointer;
            color: #1abc9c;
            font-size: 14px;
            transition: color 0.3s;
        }
        .task-list button.edit {
            color: #f39c12;
        }
        .task-list button.delete {
            color: #e74c3c;
        }
        .task-list button.mark-completed {
            color: #3498db;
        }
        .task-list button:hover {
            color: #16a085;
        }
        .task-list button.edit:hover {
            color: #e67e22;
        }
        .task-list button.delete:hover {
            color: #c0392b;
        }
        .task-list button.mark-completed:hover {
            color: #2980b9;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>To-Do List</h2>
        <div class="task-input">
            <input type="text" id="taskInput" placeholder="Add a new task">
            <button onclick="addTask()">Add</button>
        </div>
        <ul id="taskList" class="task-list"></ul>
    </div>

    <script>
        const colors = ['#FFABAB', '#FFC3A0', '#D5AAFF', '#D0F4DE', '#FCE3E3'];
        const fonts = ['Roboto', 'Arial', 'Georgia', 'Courier New', 'Tahoma'];

        function getRandomElement(arr) {
            return arr[Math.floor(Math.random() * arr.length)];
        }

        function addTask() {
            const taskInput = document.getElementById('taskInput');
            const taskText = taskInput.value.trim();
            if (taskText === '') return;

            const taskList = document.getElementById('taskList');
            const taskItem = document.createElement('li');
            
            const taskSpan = document.createElement('span');
            taskSpan.textContent = taskText;
            taskSpan.style.color = getRandomElement(colors);
            taskSpan.style.fontFamily = getRandomElement(fonts);
            taskSpan.addEventListener('click', function() {
                taskItem.classList.toggle('completed');
            });

            const markCompletedButton = document.createElement('button');
            markCompletedButton.textContent = 'Mark as Completed';
            markCompletedButton.classList.add('mark-completed');
            markCompletedButton.addEventListener('click', function() {
                taskItem.classList.add('completed');
            });

            const editButton = document.createElement('button');
            editButton.textContent = 'Edit';
            editButton.classList.add('edit');
            editButton.addEventListener('click', function() {
                const newTaskText = prompt('Edit task', taskSpan.textContent);
                if (newTaskText !== null) {
                    taskSpan.textContent = newTaskText.trim();
                }
            });

            const deleteButton = document.createElement('button');
            deleteButton.textContent = 'Delete';
            deleteButton.classList.add('delete');
            deleteButton.addEventListener('click', function() {
                taskList.removeChild(taskItem);
            });

            taskItem.appendChild(taskSpan);
            taskItem.appendChild(markCompletedButton);
            taskItem.appendChild(editButton);
            taskItem.appendChild(deleteButton);
            taskList.appendChild(taskItem);

            taskInput.value = '';
        }
    </script>
</body>
</html>
