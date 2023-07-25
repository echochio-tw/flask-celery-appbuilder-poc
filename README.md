# Celery and Flask App Builder -- P.O.C for Integration

To check integration:
1. Have redis up and running on port 6379. *(you can use docker and map the ports)*
   ```bash
    docker pull redis
    docker run -p 6379:6379 redis
   ```
2. git clone and Create a virtual environment:
   ```bash
    git clone https://github.com/echochio-tw/flask-celery-appbuilder-poc.git
    mv flask-celery-appbuilder-poc app
    cd app
    virtualenv -p python3 env
    source env/bin/activate
   ````
3. Install requirements:
    ```bash
    python -m pip install --upgrade pip
    cat requirements.txt | grep --invert-match pkg-resources | xargs -n 1 pip install
    ```
4. Crate admin and Run celery worker:
    ```bash
    flask fab create-admin
    celery -A app.celery worker &
    ```
5. Run the application:
    ```bash
    flask run --with-threads --reload --port=5003
    ```
6. Go to any path which isn't defined in the app, let's say : http://localhost:5003/
