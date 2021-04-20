# Docker-Flask-Container
A tutorial on how to make a Docker Image for a Flask application then run it in a container.

The "steps" that you follow are like this, you code the app, microservice .. then you make a docker image for it and aftewards you can run the image in a container.

Dockerfile -- build ---> Docker Image -- run ---> Container

# The application

For the application part we have a simple Flask application that starts a server on the default port.

```python
from flask import Flask

app = Flask(__name__)
@app.route("/")

def hello():
    return "hello beautiful world!"

if __name__ == "__main__":
    app.run(host="0.0.0.0")
```

# The Docker Image

Ok we have the application code now we need make an image for it. A docker image is simply a file compromised of multiple layers, that is used to execute code in Docker container.

```
FROM python:3.6.1-alpine
RUN pip install flask
CMD [ "python", "app.py" ]
COPY app.py /app.py
```

// Todo: explain all the steps from the Dockerfile

# Build the Image and Run the Container

Now that we have the image we can build it in order to have the container
```
docker build -t flask-tutorial:latest .
```

And now we have the container which we can run
```
docker run -d -p 5000:5000 flask-tutorial
```
