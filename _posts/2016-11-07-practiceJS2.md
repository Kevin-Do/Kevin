---
layout: post
title: "Practical Javascript 2"
image: "https://raw.githubusercontent.com/loverajoel/jstips/gh-pages/resources/jstips-header-blog.gif"
categories:
  - CS
  - Learning
tags:
  - Javascript
  - Vanilla
  - Training
---

# Practical Javascript 2
---
**Version 8 Implementation**  

Continued training with handlers, inputs and HTML elements.
Partitioned code and organized objects for specific purposes. (Data, DOM, View)
```javascript
//View object and removed consolelog lines
var todoList = {
  todos: [],

  add: function(todoText){
    this.todos.push({
      todoText: todoText,
      completed: false,
    });
  },
  edit: function(position, newValue){
    this.todos[position].todoText = newValue;
  },
  delete: function(position){
    this.todos.splice(position, 1);
  },
  toggleCompleted: function(position){
    var todo = this.todos[position];
    todo.completed = !todo.completed;
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
  }
};

var handlers = {
  addTodo: function(){
    var addTodoText = document.getElementById('addTodoTextInput');
    todoList.add(addTodoText.value);
    addTodoText.value = '';
    view.displayTodos();
  },
  changeTodo: function(){
    var changeTodoText = document.getElementById('changeTodoText');
    var changeTodoPosition = document.getElementById('changeTodoPosition');
    todoList.edit(changeTodoPosition.valueAsNumber, changeTodoText.value);
    changeTodoText.value = '';
    changeTodoPosition.value = '';
    view.displayTodos();
  },
  deleteTodo: function(){
    var deleteTodoPosition = document.getElementById('deleteTodoPosition');
    todoList.delete(deleteTodoPosition.valueAsNumber);
    deleteTodoPosition.value = '';
    view.displayTodos();
  },
  toggleCompleted: function(){
    var togglePosition = document.getElementById('toggleCompletedPosition');
    todoList.toggleCompleted(toggleCompletedPosition.valueAsNumber);
    togglePosition.value = '';
    view.displayTodos();
  },
  toggleAll: function(){
    todoList.toggleAll();
    view.displayTodos();
  }
};

var view = {
  displayTodos: function(){
    var todosUl = document.querySelector('ul');
    todosUl.innerHTML = '';
    for(var i = 0; i < todoList.todos.length; i++){
      var todosLi = document.createElement('li');

      //show completed
      var todoTextWithCompleted = '';
      if (todoList.todos[i].completed === true){
        todoTextWithCompleted = '(x) ' + todoList.todos[i].todoText;
      }
      else{
        todoTextWithCompleted = '( ) ' + todoList.todos[i].todoText;
      }
      todosLi.textContent =  todoTextWithCompleted;
      todosUl.appendChild(todosLi);
    }
  }
};

```
---
**Functions within Functions**  

```javascript

//Run with Debugger
function runWithDebugger(functionName){
  debugger;
  functionName();
}

function example(){
  for(var i = 0; i < 10; i++){
    console.log(i);
  }  
}
runWithDebugger(example(){
  ...
});

// Time out
setTimeout(function(){
  ...
}, 5000 //time to wait
)

//For Each
students = ['dog', 'cat'];
students.forEach(functionName(){
  ...
})
// also works with anonymous functions
function forEach(myArray, myFunction){
  for(var i = 0; i < myArray.length; i++){
    myFunction(myArray[i]);
  }
}

DOM.addEventListener('click', function(event){
  console.log(event);
});

//outputs MouseEvent{...}
```

---
**Higher Order Functions & Callbacks**

1. Functions that accept other functions
2. Enhances other functions
3. Call back functions are functions that get passed into higher order functions
