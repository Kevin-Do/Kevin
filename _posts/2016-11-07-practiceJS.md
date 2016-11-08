---
layout: post
title: "Practical Javascript"
image: "https://raw.githubusercontent.com/loverajoel/jstips/gh-pages/resources/jstips-header-blog.gif"
categories:
  - CS
  - Learning
tags:
  - Javascript
  - Vanilla
  - Training
---

# Practical Javascript
---
Watch and learn how to build a to do list from the ground up in Javascript. Starting with primative requirements and growing with important Javascript practices.  

**Requirements:**  

* Store task
* Display task
* Add task
* Edit task
* Delete task  

**Version 1 Implementation**  

```javascript
//Store:
var todos = ["item 1", "item 2"];
//Display:
console.log("My Todos: ", todos)  
//Add:
todos.push("item 3")
//Edit:
todos['desired item index'] = "item updated"
//Delete:
todos.splice('index','quantity')
```

---

**Version 2 Implementation**  


```javascript
//Display
function displayTodos(){
  console.log("My Todos: ", todos);
}  
//Add
function addTodos(item){
  todos.push(item);
  displayTodos();
}
//Edit
function changeTodos(position, newValue){
  todos[position] = newValue;
  displayTodos();
}
//Delete
function deleteTodos(position){
  todos.splice(position, 1);
  displayTodos();
}  
```
---

**Version 3 Implementation**  

```javascript
//Example Object with methods
  var todoList = {
  todos: ["item 1", "item2"],
  display: function(){
    console.log("My todos: ", this.todos);
  },
  add: function(item){
    this.todos.push(item);
    this.display();
  }
  edit: function(position, newValue){
    this.todos[position] = newValue;
    this.display();
  },
  delete: function(position){
    this.todos.splice(position, 1);
    this.display();
  }
};

```
---

**Version 4 Implementation**  

```javascript
//Add objects and alter properties(bool)
var todoList = {
  todos: ["item 1", "item2"],
  display: function(){
    console.log("My todos: ", this.todos);
  },
  add: function(todoText){
    this.todos.push({
      todoText: todoText,
      completed: false,
    });
    this.display();
  },
  edit: function(position, newValue){
    this.todos[position].todoText = newValue;
    this.display();
  },
  delete: function(position){
    this.todos.splice(position, 1);
    this.display();
  },
  toggleCompleted: function(position){
    var todo = this.todos[position];
    todo.completed = !todo.completed;
  }
};
```
---
**Version 5 Implementation**  

```javascript
//Logic and completed fields
var todoList = {
  todos: [],

  display: function(){
    if(this.todos.length === 0){
      console.log("You have no todos!");
    }
    else {
      console.log("My todos: ");
      for(var i = 0; i < this.todos.length; i++){
        if(this.todos[i].completed === true){
          console.log("(x) ", this.todos[i].todoText);
        }
        else {
          console.log("( ) ", this.todos[i].todoText);
        }
      }
    }
  },
  add: function(todoText){
    this.todos.push({
      todoText: todoText,
      completed: false,
    });
    this.display();
  },
  edit: function(position, newValue){
    this.todos[position].todoText = newValue;
    this.display();
  },
  delete: function(position){
    this.todos.splice(position, 1);
    this.display();
  },
  toggleCompleted: function(position){
    var todo = this.todos[position];
    todo.completed = !todo.completed;
    this.display();
  }
};

```
---

**Version 6 Implementation**  

Object comparisons use memory addresses.

```javascript
// Linked buttons to html DOM

var todoList = {
  todos: [],

  display: function(){
    if(this.todos.length === 0){
      console.log("You have no todos!");
    }
    else {
      console.log("My todos: ");
      for(var i = 0; i < this.todos.length; i++){
        if(this.todos[i].completed === true){
          console.log("(x) ", this.todos[i].todoText);
        }
        else {
          console.log("( ) ", this.todos[i].todoText);
        }
      }
    }
  },
  add: function(todoText){
    this.todos.push({
      todoText: todoText,
      completed: false,
    });
    this.display();
  },
  edit: function(position, newValue){
    this.todos[position].todoText = newValue;
    this.display();
  },
  delete: function(position){
    this.todos.splice(position, 1);
    this.display();
  },
  toggleCompleted: function(position){
    var todo = this.todos[position];
    todo.completed = !todo.completed;
    this.display();
  },
  toggleAll: function(){
    var totalTodos = this.todos.length;
    var completedTodos = 0;
    for(var i = 0; i < totalTodos; i++){
      if(this.todos[i].completed === true){
        completedTodos++;
      }
    }
    //all true
    if(completedTodos === totalTodos){
      //make false
      for(var i = 0; i < totalTodos; i++){
        this.todos[i].completed = false;
      }
    }
    else{
      for(var i = 0; i < totalTodos; i++){
        this.todos[i].completed = true;
        completedTodos++;
      }
    }
    this.display();
  }
};

var displayTodosButton = document.getElementById('displayTodosButton');
var toggleAllButton = document.getElementById("toggleAllTodosButton");

displayTodosButton.addEventListener('click', function(){
  todoList.display();
});
toggleAllButton.addEventListener('click', function(){
  todoList.toggleAll();
});

```

HTML:  
```html
<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Hello TODOS!</h1>
    <button id = 'displayTodosButton'> Display </button>
    <button id = 'toggleAllTodosButto'> Toggle All </button>

  <script src="script.js"></script>
  </body>

</html>

```
---

**Version 7 Implementation**  
Adding handlers:  
```html

<!DOCTYPE html>
<html>

  <head>
    <link rel="stylesheet" href="style.css">
  </head>

  <body>
    <h1>Hello TODOS!</h1>
    <button onclick='handlers.displayTodos()'> Display Todos</button>
    <button onclick='handlers.toggleAll()'> Toggle All</button>
  <script src="script.js"></script>
  </body>

</html>
```
```javascript
// Code goes here

var todoList = {
  todos: [],

  display: function(){
    if(this.todos.length === 0){
      console.log("You have no todos!");
    }
    else {
      console.log("My todos: ");
      for(var i = 0; i < this.todos.length; i++){
        if(this.todos[i].completed === true){
          console.log("(x) ", this.todos[i].todoText);
        }
        else {
          console.log("( ) ", this.todos[i].todoText);
        }
      }
    }
  },
  add: function(todoText){
    this.todos.push({
      todoText: todoText,
      completed: false,
    });
    this.display();
  },
  edit: function(position, newValue){
    this.todos[position].todoText = newValue;
    this.display();
  },
  delete: function(position){
    this.todos.splice(position, 1);
    this.display();
  },
  toggleCompleted: function(position){
    var todo = this.todos[position];
    todo.completed = !todo.completed;
    this.display();
  },
  toggleAll: function(){
    var totalTodos = this.todos.length;
    var completedTodos = 0;
    for(var i = 0; i < totalTodos; i++){
      if(this.todos[i].completed === true){
        completedTodos++;
      }
    }
    //all true
    if(completedTodos === totalTodos){
      //make false
      for(var i = 0; i < totalTodos; i++){
        this.todos[i].completed = false;
      }
    }
    else{
      for(var i = 0; i < totalTodos; i++){
        this.todos[i].completed = true;
        completedTodos++;
      }
    }
    this.display();
  }
};

var handlers = {
  displayTodos: function(){
    todoList.display();
  },
  toggleAll: function(){
    todoList.toggleAll();
  }
};


```
