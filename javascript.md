# Common JavaScript Uses for Interacting with HTML

Here are common things JavaScript does with HTML content:

## 1) Change text content
```js
document.getElementById("title").textContent = "Hello JavaScript";
```

## 2) Change HTML structure
```js
document.getElementById("box").innerHTML = "<b>New bold text</b>";
```

## 3) Change CSS style
```js
document.getElementById("box").style.color = "blue";
document.getElementById("box").style.backgroundColor = "yellow";
```

## 4) Add or remove CSS classes
```js
const card = document.querySelector(".card");
card.classList.add("active");
card.classList.remove("hidden");
card.classList.toggle("dark-mode");
```

## 5) Show or hide elements
```js
const menu = document.getElementById("menu");
menu.style.display = "none";   // hide
menu.style.display = "block";  // show
```

## 6) Handle user events (click, input, submit)
```js
document.getElementById("btn").addEventListener("click", () => {
  alert("Button clicked!");
});
```

## 7) Read input values
```js
const name = document.getElementById("nameInput").value;
console.log(name);
```

## 8) Create and add new elements
```js
const li = document.createElement("li");
li.textContent = "New item";
document.getElementById("list").appendChild(li);
```

## 9) Remove elements
```js
document.getElementById("oldItem").remove();
```

## 10) Update attributes
```js
const img = document.getElementById("photo");
img.setAttribute("src", "new-image.jpg");
img.setAttribute("alt", "Profile photo");
```

## 11) Form validation
```js
const email = document.getElementById("email").value;
if (!email.includes("@")) {
  alert("Please enter a valid email.");
}
```

## 12) Simple animations
```js
const box = document.getElementById("box");
box.style.transition = "transform 0.3s";
box.style.transform = "scale(1.1)";
```

---

Tip: Most interactions start with selecting elements:
```js
document.getElementById("idName");
document.querySelector(".className");
document.querySelectorAll("p");
```

## Mini Project Example: To-Do List

This one example uses many common interactions:
- read input value
- handle button click
- create new HTML element
- add class and style
- mark item as done
- remove item

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Simple To-Do List</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 500px;
      margin: 40px auto;
      line-height: 1.5;
    }
    h1 {
      margin-bottom: 12px;
    }
    .row {
      display: flex;
      gap: 8px;
    }
    input {
      flex: 1;
      padding: 8px;
    }
    button {
      padding: 8px 12px;
      cursor: pointer;
    }
    ul {
      list-style: none;
      padding: 0;
      margin-top: 16px;
    }
    li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 8px;
      border: 1px solid #ddd;
      margin-bottom: 8px;
      border-radius: 6px;
    }
    .task-text.done {
      text-decoration: line-through;
      color: #888;
    }
    .actions {
      display: flex;
      gap: 6px;
    }
  </style>
</head>
<body>
  <h1>My To-Do List</h1>

  <div class="row">
    <input id="taskInput" type="text" placeholder="Enter a task..." />
    <button id="addBtn">Add</button>
  </div>

  <ul id="taskList"></ul>

  <script>
    const taskInput = document.getElementById("taskInput");
    const addBtn = document.getElementById("addBtn");
    const taskList = document.getElementById("taskList");

    function addTask() {
      const taskText = taskInput.value.trim();

      if (taskText === "") {
        alert("Please enter a task.");
        return;
      }

      // Create list item
      const li = document.createElement("li");

      // Task text
      const span = document.createElement("span");
      span.textContent = taskText;
      span.classList.add("task-text");

      // Action buttons container
      const actions = document.createElement("div");
      actions.classList.add("actions");

      // Done button
      const doneBtn = document.createElement("button");
      doneBtn.textContent = "Done";
      doneBtn.addEventListener("click", () => {
        span.classList.toggle("done");
      });

      // Delete button
      const deleteBtn = document.createElement("button");
      deleteBtn.textContent = "Delete";
      deleteBtn.addEventListener("click", () => {
        li.remove();
      });

      actions.appendChild(doneBtn);
      actions.appendChild(deleteBtn);
      li.appendChild(span);
      li.appendChild(actions);
      taskList.appendChild(li);

      // Clear input
      taskInput.value = "";
      taskInput.focus();
    }

    // Add task on button click
    addBtn.addEventListener("click", addTask);

    // Add task when Enter key is pressed
    taskInput.addEventListener("keydown", (event) => {
      if (event.key === "Enter") {
        addTask();
      }
    });
  </script>
</body>
</html>
```

How to run:
1. Copy the code into a new file, for example `todo.html`.
2. Open `todo.html` in your browser.
3. Type a task, then click `Add` or press Enter.
