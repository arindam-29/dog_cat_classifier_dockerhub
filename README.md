# Dog Cat Classifier
Build a Dog cat Classifier and publish to Dockerhub:

This is a Dog Cat Classifier that uses image classification to distinguish between images of dogs and cats.

## Getting Started

### Prerequisites

Before you begin, make sure you have [Docker](https://docs.docker.com/get-docker/) installed on your machine and a [Docherhub](https://hub.docker.com/) account.

### Setting up a Virtual Environment

1. Create a python virtual environment: [For this example use python version 3.7]

    ```bash
    python3 -m venv venv
    ```

2. Activate the virtual environment:

    ```bash
    source venv/bin/activate
    ```

3. Install the required dependencies:

    ```bash
    pip3 install -r requirements.txt
    ```

## Containerization with Docker

### Building the Docker Image

To containerize the Dog Cat Classifier using Docker, follow these steps:

1. Create a Dockerfile in the root of your project with the following content:

    ```dockerfile
    FROM python:3.7.16
    COPY . /app
    WORKDIR /app
    RUN pip install --no-cache-dir -r requirements.txt
    EXPOSE $PORT
    CMD gunicorn --workers=4 --bind 0.0.0.0:$PORT clientApp:app
    ```

2. Build the Docker image using the following command (replace `<image_name>` with your desired image name):

    ```bash
    docker build -t <image_name> .
    ```
    ```
    for example: docker build -t arindam29/dog-cat:ver1 .
    ```
3. Run the Docker container:

    ```bash
    docker run -p 9000:9000 -e PORT=9000 <image_name>
    ```
    ```
    for example: docker run -p 9000:9000 -e PORT=9000 arindam29/dog-cat:ver1
    ```

4. Open url http://0.0.0.0:9000 to interact with it

5. Publish the image in DockerHub (Make sure the image name contains docuerhub account id, e.g arindam29/dog-cat:ver1)

    ```bash
    docker push <image_name>
    ```
    ```
    for example: docker push arindam29/dog-cat:ver1
    ```

Now, your Dog Cat Classifier is running inside a Docker container.

Feel free to explore and enhance the classifier as needed. Happy classifying! 🐶🐱
