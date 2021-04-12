# DroneRush
    A simple API to create Drone Competitions made with Django REST Framework.

## Project Setup

    Just Copy the Following Commands

    ```
    mkdir Dronerush
    cd Dronerush
    python -m venv env
    ./env/scripts/activate
    git clone https://github.com/falcon-Z/dronerush.git
    cd dronerush
    pip install -r requirements.txt
    ```
    The commands above will do the following
    1. Creates a directory `Dronerush`
    2. Creates a python virtual environment `env`
    3. Activates the environemtn in shell
    4. Clones the project repo from github
    5. Installs all the required packages for the project

    ### Create Superuser

        You would require an user account to access some resourses so use the following command  to create a admin user.

        ```
        python manage.py createsuperuser
        ```
        Enter username: `Admin` or something else
        Enter email: `admin@example.com`
        Enter password and confirm password

    ### Create other Users

        open django shell

        ```
        from django.contrib.auth.models import User

        user = User.objects.create_user('user01', 'user01@example.com', 'user01password')user.save()
        ```

### Token Authentication

    To Access `"pilots": "http://127.0.0.1:8000/pilots/"` You would need an access token 

    Inorder to acquire an access token open django shell by
    ```
    python manage.py shell
    ```

    then pase the following code
    ```
    from rest_framework.authtoken.models import Token 
    from django.contrib.auth.models import User 

    # Replace user01 with the name you configured for this user 
    user = User.objects.get(username="user01") 
    token = Token.objects.create(user=user) 
    print(token.key) 
    ```

    Copy the generated code  then `quit()` the shell 
    use either the `http` or `curl` to access the resources
    ```
    http :8000/pilots/ "Authorization: Token PASTE-TOKEN-HERE"
    ```
    Or
    ```
    curl -iX GET http://localhost:8000/pilots/ -H "Authorization: Token    PASTE-TOKEN-HERE"
    ```