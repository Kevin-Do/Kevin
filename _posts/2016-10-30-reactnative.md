---
layout: post
title: "React Native w/ Exponent"
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
  - Exponent
---

# "Learn Once, Write Anywhere"
- Tom Occhino

<iframe width="560" height="315" src="https://www.youtube.com/embed/2d0z_L4oXt8" frameborder="0" allowfullscreen></iframe>

React Native does not just wrap HTML, it uses 100% native views.

JSX code compiles to JS and is loaded in JavaScriptCore this is then rendered in native components.  

| JSX - > | JS - > | JavaScriptCore - > | iOS Objective C or Android Java |  

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


**Example of a Stateless Functional Component**

{% highlight yaml %}

import {Component} from 'react'
class TaskRow extends Component{
  render(){
    return (<p>{props.text}</p>);
  }
}
export default TaskRow;


var TaskRow = (prop) => {
    return <p> {props.text}</p>
};
export default TaskRow;  

{% endhighlight %}

[Javascript and JSX Linting](http://eslint.org/docs/user-guide/integrations)  


**Container vs. Presentation Components**  

| Container Components | Presentation Components |
| --- | --- |
| Can make changes to State | Receive data only though props |
|Pass functions and data to Presentation | Call backs on functions provided by props |

**Installing React Native on Windows**  

run Administrative cmd.exe - >  

*@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"*  

choco install nodejs.install  
choco install python2  
npm install -g react-native-cli

[Installation](https://facebook.github.io/react-native/docs/getting-started.html)
