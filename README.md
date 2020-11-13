# Deploying a Flask API

This project is about containerizing and deploying Flask APIs to a Kubernetes cluster using Docker, AWS EKS, CodePipeline, and CodeBuild.

Our Flask app consists of three endpoints:

- `GET '/'`: This is a simple health check, which returns the response 'Healthy'. 
- `POST '/auth'`: This takes a email and password as json arguments and returns a JWT based on a custom secret.
- `GET '/contents'`: This requires a valid JWT, and returns the un-encrpyted contents of that token. 

The built-in Flask server is adequate for local development, but not production, so we have used production-ready [Gunicorn](https://gunicorn.org/) server when deploying the app.

## Dependencies

- Docker Engine
    - Installation instructions for all OSes can be found [here](https://docs.docker.com/install/).
    - For Mac users, if you have no previous Docker Toolbox installation, you can install Docker Desktop for Mac. If you already have a Docker Toolbox installation, please read [this](https://docs.docker.com/docker-for-mac/docker-toolbox/) before installing.
 - AWS Account
     - You can create an AWS account by signing up [here](https://aws.amazon.com/#).
     
## Project Steps

Completing the project involves following steps:

1. Write a Dockerfile for a Flask app
2. Build and test the container locally
3. Create an EKS cluster
4. Store a secret using AWS Parameter Store
5. Create a CodePipeline pipeline triggered by GitHub checkins
6. Create a CodeBuild stage which will build, test, and deploy your code

## Testing

Our AWS CodePipeline already has unit tests included. Additionally, i have created a postman collection (eks-deployment.postman_collection.json) to test the apis.

Note: Please change the post body in the cllection to validate it for different values.
