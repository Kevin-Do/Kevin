---
layout: post
title: "React JS"
image: "http://mjw56.github.io/content/images/2015/05/react_native.png"
categories:
  - Learning
  - Projects
  - Courses
tags:
  - Javascript
  - React
  - Redux
  - Fundamentals
---
# React: The Right Way
---

**Architecture**

A React application is composed by a set of components. The inputs to components properties and referred to as **props** or **state**.  

State is different from props because it can change. It is best to design around components that don't use state. Props and state collectively represent the **model**. The **Document Object Model** is rendered from this model.  

You can change the DOM by changing the model. **Events** can trigger state changes. These state changes sparks another render loop. React sustains a fake DOM abstraction. The changes are then updated to the real DOM is the most efficient way possible.  

* React & Knockout JS
  * Both provide:
   * Rendering to DOM
   * Events
* React & Angular & Ember
  * Larger and more generalized
* React & Backbone
    * Common to use React as alternate view for Backbone

**Components**

Each component corresponds to an element in the DOM. Components can be **nested**. Same interaction for the DOM elements.  

Top level namespace is React. Minimum requirement is a render function.

| Aspects | Description |
| --- | --- |
| JSX | Allows us to write HTML like syntax which gets transformed to lightweight JavaScript objects.  | 
| Virtual DOM | A JavaScript representation of the actual DOM.  |
| React.createClass | The way in which you create a new component.  |
| render (method) | What we would like our HTML Template to look like.  
| ReactDOM.render | Renders a React component to a DOM node.  
| state | The internal data store (object) of a component.  
| getInitialState | The way in which you set the initial state of a component.  
| setState | A helper method for altering the state of a component.  
| props | The data which is passed to the child component from the parent component.  
| propTypes | Allows you to control the presence, or types of certain props passed to the child  component.  |
| getDefaultProps | Allows you to set default props for your component. |

| Component LifeCycle  |
| --- |
| componentWillMount — Fired before the component will mount |
| componentDidMount — Fired after the component mounted  |
| componentWillReceiveProps — Fired whenever there is a change to props |  
| componentWillUnmount — Fired before the component will unmount |
| Events  |
| onClick  |
| onSubmit  |
| onChange  |
