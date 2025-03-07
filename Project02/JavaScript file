document.addEventListener("DOMContentLoaded", () => {
    const taskForm = document.getElementById("task-form");
    const taskList = document.getElementById("task-list");
    let tasks = [];

    taskForm.addEventListener("submit", (event) => {
        event.preventDefault();
        const title = document.getElementById("task-title").value;
        const priority = document.getElementById("task-priority").value;
        const status = document.querySelector("input[name='task-status']:checked").value;
        
        const task = { title, priority, status };
        tasks.push(task);
        renderTasks();
        taskForm.reset();
    });

    function renderTasks() {
        taskList.innerHTML = "";
        tasks.forEach((task, index) => {
            const li = document.createElement("li");
            li.classList.add("list-group-item", "d-flex", "justify-content-between", "align-items-center", "task-item");
            li.innerHTML = `
                <span class="${task.status === "completed" ? "text-decoration-line-through" : ""}">
                    ${task.title} - <strong>${task.priority}</strong> - ${task.status}
                </span>
                <div>
                    <button class="btn btn-success btn-sm complete-task" data-index="${index}">Complete</button>
                    <button class="btn btn-danger btn-sm remove-task" data-index="${index}">Remove</button>
                </div>
            `;

           
            switch(task.priority) {
                case 'high':
                    li.style.backgroundColor = "#f8d7da"; 
                    break;
                case 'medium':
                    li.style.backgroundColor = "#fff3cd"; 
                    break;
                case 'low':
                    li.style.backgroundColor = "#d4edda"; 
                    break;
            }

            taskList.appendChild(li);
        });
    }

    taskList.addEventListener("click", (event) => {
        if (event.target.classList.contains("remove-task")) {
            const index = event.target.getAttribute("data-index");
            if (confirm("Are you sure you want to remove this task?")) {
                tasks.splice(index, 1);
                renderTasks();
            }
        }
        
        if (event.target.classList.contains("complete-task")) {
            const index = event.target.getAttribute("data-index");
            tasks[index].status = "completed";
            renderTasks();
        }
    });

    
    const clearCompletedBtn = document.createElement("button");
    clearCompletedBtn.classList.add("btn", "btn-warning", "mt-3");
    clearCompletedBtn.innerText = "Clear Completed Tasks";
    document.body.appendChild(clearCompletedBtn);

    clearCompletedBtn.addEventListener("click", () => {
        tasks = tasks.filter(task => task.status !== "completed");
        renderTasks();
    });
});
