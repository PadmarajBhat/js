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
    * @viewChild and ngAfterViewInit: Parent peeps into child class variable on its own as if to hack the values.
        * child does no special operation except that it populates its own regular class variable( with no special decorator)
        * but this requires parent to wait till child executes.

* service : 
    * is a method to retain the data from a component and reuse the same in other or same component.
    * However, its scope is limited to single page application life. i.e. if the page refreshes then it looses the value.
        * the service is out of any component like a global variable/service, Dependency injection gives the start of the object initation and subsequent access of object variable and methods. when you reload entire thing goes for refresh and hence the value too.
    * As it is injected to a component (and not local variable) it stays with latest value even after returning from a component and thus availing the values to other component where it is *Injected*.
        * to retain the value of the service even after refresh db, file, local storage and session storage can be used.
    * fortifying the above through stackoverflow ans
        * https://stackoverflow.com/questions/28846266/ionic-local-storage-vs-using-service
        * https://alligator.io/js/introduction-localstorage-sessionstorage/
            * from the scope perspective service < sessionStorage < localStorage

* button vs hyperlink:
    * from the flexibility of the action on clicking link, button has more support than hyperlink
        * performing set of operartion and then emitting an event through button but not through hyperlink ...is it ? Perhaps this is not the right answer. I guess there can be events on hyperlink too !!!
        * angular buttons : https://material.angular.io/components/button/examples
        
* ng-form : aggregates form-control class
* form-control: lets us have validation on the input field
    ```
    <input id="name" name="name" class="form-control"
      required minlength="4" appForbiddenName="bob"
      [(ngModel)]="hero.name" #name="ngModel" >
    ```
    * input can not only take text but also file and can be submit button too
    * id is more for CSS selection and name is for what has to be sent to server in a form. name value depends on the server programming language and in compliance to it.


* https://angular.io/api/forms/NgModel : simple standard control example fails with below error
    * There is no directive with "exportAs" set to "ngModel" ("
    * resolved by adding ```FormModule``` in app.module.ts as indicated in https://stackoverflow.com/questions/38648407/angular2-error-there-is-no-directive-with-exportas-set-to-ngform

* 2 way data binding example:
    * yes it is true that the data in the view auto syncs with data in the class then where it is applicable.
        * usually in accessibility case where increase in font size immediately changes the view. Here submit button is implicit. Change in the size of the font not only changes the class variable but also view. i.e. MVVC
        * https://news.ycombinator.com/item?id=7523890: drop down selection to reflect in other boxes
    * need to decode the example to understand clearly the concept: https://stackblitz.com/angular/pyoarjpqxal?file=src%2Fapp%2Fapp.component.html
        * first it changes size is a child component variable which is being modified by parent in 2 way fashion. 
            * [(size)] ='fontSizePx' : has lead to both direction value change. 
                * First parent value goes to child (size has @Input)
                * and since it is 2 way, + or -  button increases the size variable value and also changes value of fontSizePx.
            * (sizeChange)="fontSizePx=$event" : sizeChange is the child variable where an output is expected to be kept (@Output) and hence parent component fontSizePx variable is listening for the event which child would emit. In this example, illustration is done to show how it had to be done without 2 way data binding.
* https://medium.com/better-programming/what-is-the-difference-between-for-in-and-for-of-in-javascript-650952654e97
    * for...in for enumerables
    * for ...of for iterators
* https://towardsdatascience.com/3-python-libraries-you-cant-miss-in-2020-2ee4a7277cf1
    * python_dateutil : to parse date string in a string
    * Markdown: to converty markdown to html
    * colorama: coloring pring statements
* Observables and its subscribers : https://medium.com/@luukgruijs/understanding-creating-and-subscribing-to-observables-in-angular-426dbf0b04a3
    * it is used for transmitting messages from publisher to subscriber.
    * key difference between observable to promises is that observables can send multiple values to subscriber.
    * it is a lazy evaluation and hence till the subscribed it wont evaluate.

* facing issue:  Property 'map' does not exist on type 'Observable<Response>'
        * stackoverflow suggests : npm install --save rxjs-compat@6
        * *ans* : subscriber has to be given to any observable. subscriber can listen to observable and *next* function can assign the value from observable to class variable.

* facing issue: subscriber is asynchronous call. statements below to it is executed before to subscribe next function execution
    * subscribe function as 3 parameters : next, err and completion. all the 3 are functions as arguments. Anything in completion will be executed last.
    
* i#3 : constructor waiting for backend to serve the data ends up executing the html before to api response.
    * **1**: convert the observable to promise and wait on it
        * use http.get().toPromise() to convert the observable to promise. It works for the case when api returns only one value and not multiple.
        * now that we have to wait on it use *await* before the get call: await http.get().toPromise()
        * since we need to use await, move the code to a seperate function and define it as *async*
    * **2** : use the service class variable in the component template (html)
        * service is injected to the component through dependency injection (constructor argument).
        * thus we have access to the variables of the service in the component.
        * like http.serviceVariable in the template [direct reference through dot operator].
        * this avoids the local variable and removes the complexity of syncing service and local component class variable
        * code condenses heavily !!!
        
* i#4 : html for tag does not read the latest class variable value
    * *Ans*: the html reads the class variable correctly. it is the service which does the async call and hence service class variable does not gets an update but it is returned as an empty array. i#3 solves the issue
    
* **dialogflow**:
    * it requires key file to be downloaded from google cloud.
    * in that file private key will be in the form of : ---begin......---end---\n
        * it has to be copied as is or else you would get error :https://github.com/googleapis/google-cloud-node/issues/2658

* i#5 : how dow we handle the async func calls in express router
    * *ans*: in the router.get("/url", **async**(req,res,next){});

* **CSS**: 
    * box-shadow : gives the border and shadow to the *div* or *span*
    * *div* directly has the *align=center* option which can be handy in placing the chat window *div* at the center of the page.
    * when placed in a single *div* , *input* and *button* align inline.
    * *padding* is handly when u want the item to be a distant away from the border. The padding can be applied both to the page or a small span.
    * *float* is handy to right align or left align : for user and bot text alignment in chat window.
    * *width* and *height* of the div determines the box parameter of the div.

* **route guard**:
    * helps us to control the navigation: like only through parent component the current component has to be loaded i.e. only after login, load the home page.
        * ng generate guard auth/auth :  to generate 2 files in auth folder : auth.guard.ts and auth.guard.spec.ts
        * a constructor might not be there, create one : constructor(private router: Router) {}
            * you may have to include Router in the import under @angular/router
        * in the router file, there are already path url defined:
        ```
        { path: 'xyz', component: XyzComponent},
        ```
        should be changed to
        ```
        import { AuthGuard } from './auth/auth.guard';
        .
        .
        
        { path: 'xyz', component: XyzComponent, canActivate: [AuthGuard]}
        ```
        * to stop navigation directly to a url:
        ```
        canActivate(
        next: ActivatedRouteSnapshot,
        state: RouterStateSnapshot,
        ): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {

        if (state.root.component == null) {
      
        this.router.navigate(['/']);
        console.log("routing to home directory");
        return false;
      
        }
        return true;
        }
        ```
        * as u can note, the router (this) uses the DI introduced router we talked about in the previous point.
            * it was a random search for some difference between target url through parent link and direct access. I found componet to have the appcomonent class defined there for routed case. It was null in case of direct access.
            
* children routing:
    ```
    {
    path: 'reports', component: ReportsComponent,
    children: [
      //{ path: '', component: ReportsComponent },
      { path: 'recruitedby', component: RecruitedbyComponent }
    ]
    }
    ```
    * the only 2 advantages I have seen so far for parent child config are that:
        * relative reference of the url: recruitby is actually reports/recruits by
        * perhaps the state.root.component for recruitby is "reports" : for authentication purpose only

* decoding : https://www.youtube.com/watch?v=tygNPckEZbw
    * like we have *extern* in *C*, we have *declare* in *javascript*. A declaration in the current module/file indicating the some other module has the definition of the variable.
    * Now there is a debatable point :
        * the google chart script is loaded in the index.html file. This is against the lazy loading principle. Can make the initial load slower. it will have impact on performance as indicate in the intro of https://codinglatte.com/posts/angular/lazy-loading-scripts-and-styles-angular/
            * there are discussions like https://stackoverflow.com/a/50674496/8693106 which talk about the loading the scipt in the component.
            ```
            private loadExternalStyles(styleUrl: string) {
              return new Promise((resolve, reject) => {
                const styleElement = document.createElement('link');
                styleElement.href = styleUrl;
                styleElement.onload = resolve;
                document.head.appendChild(styleElement);
              });
            }
            ```
            * intuition here is that we are dynamically adding a element to already loaded html associate a promise object to it.
            * in the caller you just have to wait till the promise object to have resolved state.
            
* **services** : 
    * if present in the component, then a new instance is created each time the component is invoked. Thus cannot be used as the data holder. May be only for the services like http calls are best use cases.
    * services if not used are taken out from the final build
    * @Injectable directive makes the serivce DI capable for component

* **BootStrap**:
    * it too has card and has better variation when compared to angular material. Yesterday, I tried to use Angular Material and found it difficult to align center of the page but Bootstrap already has one dedicated for center
    * @angular/material, ng-bootstrap and bootstrap can be used simultaneously for beautiful web page :)
  * Material: we need to import the respective component at **app.module.ts** and straight away use it in needed component's html file.
  * ng-bootstrap: requires bootstrap. 
    * first install bootstrap : ```npm install bootstrap```
    * refer bootstrap in the style listing:
       * goto *node_modules* --> *bootstrap* --> css --> bootstrap.min.css then right click on the file and copy project path
       * goto **angular.json** file and in that **styles** key should have **styles.css** as one elemnt in the array, add the copied path as the second element. change the back slash to forward slash and remove anything before to **node_module** and add **../** before it.
            * You need both jquery and bootstrap in the script array
            ```
            "styles": [
              "./node_modules/@angular/material/prebuilt-themes/indigo-pink.css",
              "src/styles.css",
              "./node_modules/bootstrap/dist/css/bootstrap.min.css"
            ],
            "scripts": [
              "./node_modules/jquery/dist/jquery.min.js",
              "./node_modules/bootstrap/dist/js/bootstrap.min.js"
            ]
            ```
            * and note that if angular.json file is changed then ```ng serve``` has to be re issued. Else, there wont be any impact on the bootstrap classes in your css.
    * just with these 2 steps you could observe chanages in the render of all the component's html.
    * now install ng-bootstrap : ```npm install ng-bootstrap```
    * now either of one can be done at **app.module.ts**:
      * ```import {NgbModule} from '@ng-bootstrap/ng-bootstrap';```
      * or
      * ``` import {NgbPaginationModule, NgbAlertModule} from '@ng-bootstrap/ng-bootstrap';```

* ngStyle: 
    * when you need the page to be accessible through different device, you would want it to be flexible height and width
    * ngStyle lets you do that programatically; the class variable can set the value like
        ```
        [style.height.px]="width"
        ```
        * where width is the class variable
        * multiple attribute changes can be through object assignment like ```[ngStyle]="objExp"```
        
* to get the max height of the current device is given in : https://stackoverflow.com/a/41334303/8693106
    ```
    @Component({...})
    export class MyClass {

        myInnerHeight: window.innerHeight;
        constructor(){}

    }
    ```
    * later use this in ngStyle as indicated above
    * useful when <div> is empty and dynamically gets the value
* how to publish Angular project on github pages: https://dzone.com/articles/how-to-deploy-an-angular-application-to-github

* **RxJS** : Awesome table for pull vs push fundamentals
    * push is when data originator decides the data has to be sent to consumer
    * pull is when data originator already has the data and active consumer consumes data.

* https://material.angular.io/cdk/scrolling/api#cdk-scrolling-services: perhaps can help me detection of the direction of scrolling on a component.
    * on scroll to top on the first element give a modal display and perhaps scroll down on last element too.
* difference between DI and local variable: https://stackoverflow.com/a/5481944/8693106
* .includes : used for searching sub string in a string
