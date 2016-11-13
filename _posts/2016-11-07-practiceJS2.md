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

# Concepts  

* Handlers, inputs and HTML elements.
* Partitioning code and organized objects for specific purposes.
* (Data, DOM, View)
* Event Delegation  
* Function passing

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

---

**Event Delegation**

```javascript
//Using the event object
setUpEventListeners: function(){

  //ul delete
  var todoUl = document.querySelector('ul');
  todoUl.addEventListener('click', function(event){
    var elementClicked = event.target;
    if(elementClicked.className === 'deleteButton'){
      handlers.deleteTodo(elementClicked.parentNode.id);
    }
  });

}
```
---
**Using This**

```javascript

var objectName = {
  methodOne: function(){
    //code
    otherObject.array.forEach(function(){
      //in order to use methodTwo
      // we must add a this argument to forEach, this has a different context
    }, this // right here);
  },
  methodTwo = function(){
    //code
    //the forEach function cannot access me because it is a callback function
    //that is within a method and therefore the this is referring to methodOne
  }  
};
```
---

![Finished](http://i.imgur.com/W43ndvV.png)  
[Click Me!](https://plnkr.co/edit/XGzJDb?p=info)  
{: .btn .btn_success}  
