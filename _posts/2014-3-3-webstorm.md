---
layout: post
title: Hi WEB!
categories : [node,angular,programming,webstorm,eclipse,brackets]
---

On this blog i will share some of my experiences with different software products, programming languages, design patterns and so on. I hope you have fun reading my blog.

##### Searching for the best editor for node.js and angular.js programming
Ok, i wanted to start a new web project with the **best** tools one can get. The future is node.js :D, so i could not resist to develop with it. As it's only for the backend i searched another framework for the frontend. There are really a lot of choices, so i decided to go with angular.js. I will try react later, it is also really powerful.

##### Webstorm IDE and node.js + angular.js 
###### PART I
The Webstrom IDE suites webdevelopement with node.js and angular.js very well. If you want to start a new project you will notice, that you can choose between a node.js and an angular.js application. But we want both in one project !
I had a codebase with node.js as backend and angular.js as frontend and wanted to use it in my project. I opened the project folder in Webstorm and for the most part everything was fine. You can select your app.js or server.js and run it. Webstorm will start the node server and you can visit the webpage in your browser. 

###### But ....
if you look in your source code, you will notice, that Webstorm gives some hints to you. For example the "require" is unresolved hint.
Okay, if you create a pure node.js project from scratch, then this hint is not there, because Webstorm knows require. You even can go to the definitions. So what's up ? I searched at fist for the project settings in Webstorm. Unfortunately they are missing in Webstorm ??!! I worked previously with Intellij, also a great product from the same developer, and there was a project settings entry in the menu. Webstorm is missing this important feature :D If someone knows where I can find it, contact me.

##### Searching for a solution
Webstorm is very powerful, therefore i wanted to use all of it's features. It didn't know "require" because Webstorm uses a trick to know it. It has predefined libraries for node, and they are not active for my project. To get them to work you must edit two files in the .idea folder (in linux):

1. jsLibraryMappings.xml, add these lines:
{% highlight html %}
<file url="PROJECT" libraries="{Node.js v0.10.32 Core Modules}" />
<includedPredefinedLibrary name="Node.js Globals" />
{% endhighlight %}
2. $PROJECTNAME.iml, add these lines:
{% highlight html %}
<orderEntry type="library" name="Node.js v0.10.32 Core Modules" level="application" />
{% endhighlight %}

Replace $PROJECTNAME with the actual project name. Then reload the project in webstorm. Now you will see, that "require" is defined in webstorm and you can even jump to the definition with Ctrl+B.
