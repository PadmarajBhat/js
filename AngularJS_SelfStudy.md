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


* ```ng new app``` : creates a new app and in the sample html provided as an example has lot of basics covered in it. Good for the beginner and for tricky problem solving. 
        * for eg tricky problem : how do keep all of the example html and css code in your app but on your new component should get the entire fresh page ?
            * **ans** : move all the app.component.html entries to a new component. then include the component in routes in the app-routing.module.ts. So, now, app.component.html page only one statement ```<router-outlet></router-outlet>``` and root url maps to a new component. 
            * at this point you create another component where your business component and routelink this component from older component.
            * this would load the new component from old component and hence old components are replaced by your new component.
            * as in https://stackoverflow.com/questions/42129460/hide-parent-view-in-angular-2
* span vs div :
    * span indicates it is content within content where as div is generally encompassing bigger entities (though nesting is allowed).
        * https://stackoverflow.com/a/183536/8693106
    * when I added a box to a text and that text if part of div then the box would span to entire width of window irrespective of text size (though height is as that of text)
    * when I add a box to span then the box is limited to text only and not to entire width. Kind of what i wanted. 

* there are 3 ways of transferring data between parent and child components
    * @Input : Parent to child information transfer and not the other way. Parent should know the child class variables and should set the same in the .html file throgh <app-child> property setting. Child should have the variable declaration with @Input.
    * @Output and event emitter: Child to parent information txfr.
        * child should have @Ouput in its class variable and Parent should wait for an event from child to be emitted. Till the child gets the value for the parent variable the variable does not have any value. Child needs to trigger an event to assign the value to parent.
        * Note that there can be multiple @output in the child as in : https://stackoverflow.com/a/40023776/8693106
