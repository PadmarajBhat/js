# Node.js self study ( edureka, medium, quora, twitter etc )
* You start with ```npm init``` in a directory  where you intend your app server (backend app) development.
  * this would create ```package.json``` with user input description of the app and other details
    * this file is cruicial for containerization of the app for cloud or any deployment.
    * this step is equivalent to creating a new virtual environment in anaconda prompt for a new app development. It would help to have specified version of the package for the app without disturbing the other app packages version in other environments.
    * the **package.json** file is distantly equivanet to **requirements.txt** file in case of python development.
  * do ```npm install``` for the required packages to be used in the app
    * this is equivalent to ```pip install``` in python environment.
    * here each install automatically makes an entry into **package.json** dependency key.
  
* now that environment is ready with required packages in the node env, let us dive to coding.
  * like that of ```import``` statement in python we have ```require``` in nodejs
    * ```
         from sklearn.tree import DecisionTreeRegressor
         regr_1 = DecisionTreeRegressor(max_depth=2)
      ```
    * in the similar analogy:
      ```
         const express = require('express');
         const app = express();
      ```
    * like in **DTR** has the first argument as the function to measure the quality of the split
      ```
      criterion{“mse”, “friedman_mse”, “mae”}, default=”mse”
      ```
      * similarly we have
       ```
       app.use(cors());
       ```
       
    * like the flask app we have express
      ```
      https://www.palletsprojects.com/p/flask/
      from flask import Flask, escape, request

      app = Flask(__name__)

      @app.route('/')
      def hello():
          name = request.args.get("name", "World")
          return f'Hello, {escape(name)}!'
      ```
      
    * we have in express as 
      ```
      const express = require('express');
      const app = express();
      const router = express.Router();
      const PORT = 3000;
      
      app.listen(PORT, () => { console.log ("listening to port"+PORT);}
      
      router.get("/", (req, res, next) => {
       res.json("Welcome");
      });
      ```
* @angular/material, ng-bootstrap and bootstrap can be used simultaneously for beautiful web page :)
  * Material: we need to import the respective component at **app.module.ts** and straight away use it in needed component's html file.
  * ng-bootstrap: requires bootstrap. 
    * first install bootstrap : ```npm install bootstrap```
    * refer bootstrap in the style listing:
       * goto *node_modules* --> *bootstrap* --> css --> bootstrap.min.css then right click on the file and copy project path
       * goto **.angular-cli.json** file and in that **styles** key should have **styles.css** as one elemnt in the array, add the copied path as the second element. change the back slash to forward slash and remove anything before to **node_module** and add **../** before it.
    * just with these 2 steps you could observe chanages in the render of all the component's html.
    * now install ng-bootstrap : ```npm install ng-bootstrap```
    * now either of one can be done at **app.module.ts**:
      * ```import {NgbModule} from '@ng-bootstrap/ng-bootstrap';```
      * or
      * ``` import {NgbPaginationModule, NgbAlertModule} from '@ng-bootstrap/ng-bootstrap';```

* typeof variable : gives you the python equivalent of type(variable) output
* when an array is replied from a function, it is possible that the reciever gets the object with array indexes as keys and respective index values as the key value of the object.

* **charts**: import google charts to components
  * need to decode https://www.youtube.com/watch?v=tygNPckEZbw
