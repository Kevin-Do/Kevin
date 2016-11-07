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

**Requirements:**
  * Store task
  * Display task
  * Add task
  * Edit task
  * Delete task  

**Version 1 Implementation**  

{% highlight yaml %}  
1. Store: var todos = ["item 1", "item 2"];
2. Display: console.log("My Todos: ", todos)  
3. Add: todos.push("item 3")
4. Edit: todos['desired item index'] = "item updated"
5. Delete: todos.splice('index','quantity')

{% endhighlight %}

---

**Version 2 Implementation**  


```javascript
function displayTodos(){
  console.log("My Todos: ", todos);
}  

function addTodos(item){
  todos.push(item);
  displayTodos();
}

function changeTodos(position, newValue){
  todos[position] = newValue;
  displayTodos();
}

function deleteTodos(position){
  todos.splice(position, 1);
  displayTodos();
}  
```
