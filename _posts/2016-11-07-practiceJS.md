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





```
