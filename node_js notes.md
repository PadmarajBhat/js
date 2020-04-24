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
* typeof variable : gives you the python equivalent of type(variable) output
* when an array is replied from a function, it is possible that the reciever gets the object with array indexes as keys and respective index values as the key value of the object.

* **charts**: import google charts to components
  * need to decode https://www.youtube.com/watch?v=tygNPckEZbw
* ("A" < addressString[i] && addressString[i] < "z") :  to check if the characters are only alphabets
* !("0" <= addressString[i] && addressString[i] <= "9"): to check if char are not numbers
* process.env.NODE_TLS_REJECT_UNAUTHORIZED = "0"; enables to connect to the server with self signed vertificate.
