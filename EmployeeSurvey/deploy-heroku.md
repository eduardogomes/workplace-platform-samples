# Deploying this Thanks Bot to Heroku


1. Get a free [Heroku account](https://signup.heroku.com/) if you haven't already.

2. Install the [Heroku toolbelt](https://toolbelt.heroku.com) which will let you launch, monitor and generally control your instances (and other services like databases) from the command line. 

3. [Install Node](https://nodejs.org), this will be our server environment. Then open up your terminal and make sure you're running the latest version of npm, installed globally (the ```-g``` switch):

    ```
    sudo npm install npm -g
    ```

4. Clone this project and switch into the project directory.

    ```
    git clone https://github.com/fbsamples/workplace-platform-samples.git
    cd EmployeeSurvey
    ```

5. Install Node dependencies.

    ```
    npm install
    ```

6. Create a new Heroku application and push the code to the cloud.

    ```
    $ heroku create
    Creating app... done, ⬢ mystic-wind-83
    Created http://mystic-wind-83.herokuapp.com/ | git@heroku.com:mystic-wind-83.git
    ```  


7. Return to the repo root and distribute the application to Heroku
    ```
    cd ..
    git subtree push --prefix EmployeeSurvey heroku master
    ```

8. Set your enviroment variables according to the values set on the Workplace integration
 ![Workplace Integration](/public/img/integration.png)

    ```
    heroku config:set APP_SECRET=<value for App Secret, 1 on image above>
    heroku config:set ACCESS_TOKEN=<value for Access Token, 2 on image above>
    heroku config:set VERIFY_TOKEN=<value for Verify Token, 3 on image above>
    ```

    Also set the permissions (Mention Bot, REad group content and Manage Group Content), the callback URL on Workplace with https://<application name,  e.g.: mystic-wind-83>.herokuapp.com/webhook and "mention" subscription field.

9. You should now be able to start a survey sending a request ```GET https://<application name,  e.g.: mystic-wind-83>.herokuapp.com/start/{user-id}```.
