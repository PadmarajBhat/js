##### Angular JS described in the Udacity free course is 1.x and hence starting new note. Trying to read from The Webpage and other open sources


* Angular JS requires Node.js. 
     * Now, what is Node.js ? https://www.toptal.com/nodejs/why-the-hell-would-i-use-node-js
     * Why I need NodeJS: https://www.angularjswiki.com/angular/is-node-js-required-for-angular-2-or-angular/
          * we need to conver the typescript to javascript and angular packages are npm (node package manager) dependent.
          * The article talk about How single threaded node js is faster than java (multi threaded). It simply creates a pool of tasks and runs one by one. Here the assumption is each request asynchronous and non blocking in nature. So like bullets in gun loaded and fired, one after the other.
     * Router is one where we can navigate to different url in the module. so that we can navigate directly to it.
            * when we create a ```ng new my-app``` then the first question the client asks is router.   
            
     * The default app is an ad for angular. However, it is an good example of lot of components in angular.
            * it has interactive command display which may be using 2 way communication
            * redirection to lot of pages
                    * documentation
                    * github * rating
                    * twitter
                    * CLI documentation
                    * so many more
            * it is an example for SPA (Single page application). It would have been better to have multiple app, route, and service in the example too.

* ``` ng generate component xyz``` : can only be executed under **app/src/** directory where *app.component.* files are present
    * if we attempt outside src directory then we would get error : **Could not find an NgModule. Use the skip-import option to skip importing in NgModule.**
