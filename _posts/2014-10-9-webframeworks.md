---
layout: post
title: Hi WEB!
categories : [node,angular,programming,webstorm,eclipse,brackets]
comments: True
---

On this blog I will share some of my experiences with different software products, programming languages, design patterns and so on. I hope you have fun reading my blog.

##### Frameworks for webdevelopment
Ok, i wanted to start a new web project with the **best** tools one can get. The future is node.js :D, so i could not resist to develop with it. As it's only for the backend you need a framework for the frontend too. There are really a lot of choices. I decided to go with angular.js. I will try react later, it is also really powerful. It's said that react is more simple than angular.js, because you need to grasp only the component design pattern. It's straight forward and easy to understand, because you use the components like you would have POJOs (Plain Old Java Objects).
In angular.js you need to learn a lot of new concepts like modules, directives, injection and so on. But that's the beauty of this.

##### Searching for the best editor for node.js and angular.js programming
One of the important things left if you have choosen your frameworks, is the selection of your development tools.
If you research this issue you will find a lot of editors and IDEs for webdevelopment. A limited selection is:  
&nbsp;&nbsp;&nbsp;1. [WebStorm](https://www.jetbrains.com/webstorm/)  
&nbsp;&nbsp;&nbsp;2. [Brackets](http://brackets.io/)  
&nbsp;&nbsp;&nbsp;3. [Eclipse with Node Plugin](http://www.nodeclipse.org/)  

The editors are listed according to my preference. Some pros and cons.  
&nbsp;&nbsp;&nbsp;1. WebStorm  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\+** &nbsp;smartest IDE ever  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\+** &nbsp;complete package  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\-** &nbsp;startup is slower then the other two  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\-** &nbsp;it costs money ;-(  
&nbsp;&nbsp;&nbsp;2. Brackets  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\+** &nbsp;fast startup  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\+** &nbsp;minimalistic  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\+** &nbsp;really easy to extend with own extensions  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\-** &nbsp;without extensions not really useful  
&nbsp;&nbsp;&nbsp;3. Eclipse  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\+** &nbsp;is really flexible with a lot of plugins  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\-** &nbsp;more difficult to setup  

My favorite is WebStorm because it's by far the most intuitive and the most productive system.
Refactoring, autocompletion, helpsystem and debugging are working like a charm. You install it and it works how it is supposed to work. A little downside is that it costs money. But you can check it out for free for 30 days. Try it!

Brackets is brilliant too, but not there yet.
There is no refactoring (only simple replace), and code assistance is not as good as in Webstorm. But i liked it, because, you can extend it on the go. You can jump in the extensions code, change it, and viola you have a better editor! My first step with Brackets was writing an extension for node.js, to start all the necessary servers and debug configuration ala theseus.

The last editor is fine also, but it lacks code assistence completely without the necessary plugins. For this purpose use tern, it's okay. But if you ever used WebStrom there is no comparison. The standard version of eclipse is ugly too, you should change the theme if you don't want to hurt your eyes badly.

##### Webstorm IDE and node.js + angular.js 
The WebStrom IDE suites webdevelopement with node.js and angular.js very well. If you want to start a new project you will notice, that you can choose between a node.js and an angular.js application. But what if you want to use both at the same time ?
I had a codebase with node.js as backend and angular.js as frontend and wanted to use it in my project. I opened the project folder in WebStorm and for the most part everything was fine. You can select your app.js or server.js and run it. WebStorm will start the node server and you can visit the webpage in your browser. 

*But ....*  
if you look in your source code, you will notice, that there are some unresolved issues. For example the "require" identifier is unresolved.
Okay, if you create a pure node.js project from scratch, then this issue is not there, because WebStorm knows the identifier "require". You even can go to the definitions. So what's up ?

###### Searching for a solution
WebStorm is very powerful, therefore i wanted to use all of it's features. It didn't know "require" because Webstorm uses a trick to know it. It has predefined libraries for node, and they are not active for my project. To get them to work you must edit two files in the .idea folder (in linux):

1. jsLibraryMappings.xml, add these lines:
{% highlight html %}
<file url="PROJECT" libraries="{Node.js v0.10.32 Core Modules}" />
<includedPredefinedLibrary name="Node.js Globals" />
{% endhighlight %}
2. $PROJECTNAME.iml, add these lines:
{% highlight html %}
<orderEntry type="library" name="Node.js v0.10.32 Core Modules" level="application" />
{% endhighlight %}

Replace $PROJECTNAME with the actual project name. Then reload the project in WebStorm. Now you will see, that "require" is defined and you can even jump to the definition with Ctrl+B.

