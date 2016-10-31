---
layout: post
title: "React Native"
image: "http://mjw56.github.io/content/images/2015/05/react_native.png"
categories:
  - Learning
  - Projects
  - Courses
tags:
  - Javascript
  - Cross Platform
  - Mobile
  - React Native
---

# "Learn Once, Write Anywhere"
- Tom Occhino

React Native does not just wrap HTML, it uses 100% native views.

JSX code compiles to JS and is loaded in JavaScriptCore this is then rendered in native components.  

JSX - > JS - > JavaScriptCore - > iOS Objective C | Android Java  

{% highlight yaml %}
import {Component} from 'react';

class Cat extends Component {
    render() {
      return (
        <p>
          {this.props.name}
        </p>
        );
    }
}
export default Cat  
{% endhighlight %}

We begin with a reference to base component from 'react'. We extend the base component. Define the render function and bind the value passed though props. The class is then exported. All React components need a render function. Exported components can be reused in other components.

{% highlight yaml %}
import {Component} from 'react'
import {Cat} from "./Cat"
class Main extends Component {
    render() {
      return(
          <div>
            <Cat name="Douglas" />
          </div>
        );
    }
}
export default Main;  
{% endhighlight %}
