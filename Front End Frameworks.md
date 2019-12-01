# A Free Udacity Course that compares Angular and Ember

### 1. Features of Single page apps
* A typical single page front end application has
    * HTML Chunks
    * DOM manipulations
    * data processings
    * handle user interactions
* server side vs client side apps
     * server side app would have mostly constant data rendered at front end like blogs and contract form
     * client side app would have dynamic data like email client, searchable map and stock ticker
     * identifying the type of the app helps us to know the cost of the refresh of the single page app.  


* Angular JS Framework:
    * In a nutshell has  
            * Module : encloses the other components
            * template : holds the view part of the web page
            * scope : determines the connection between controller and template and passes it **bidirectionally**
            * controller: passes the required data for templates
            * router: interacts with multiple controller for managing the interrelated data  between controllers.


* Often in the blogs you would find the reference to [https://en.wikipedia.org/wiki/Spaghetti_code] which means nothing more than unmanaged code. And all framework makes it easier manage the code, like having the folder structure where all the dependent files go and easy coding syntax which reduces the common design hurdles.


* As clearly mentioned in the blog: https://www.lullabot.com/articles/choosing-the-right-javascript-framework-for-the-job
      * Interactive application is the main focus of the javascript. The user interactivity spans to include storing, passing and manupulating the data user shares with front end application through interaction like clicks (tap on mobile) and keyboard hits.If these interaction inputs have to go to server each time something changes then it is not only time consuming but also it is seemless user experience.
