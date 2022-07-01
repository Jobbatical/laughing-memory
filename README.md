# DevSecOps Challenge

## The context

This challenge addresses a web application with a microservice architecture to calculate the [acceleration](http://www.softschools.com/formulas/physics/acceleration_formula/1/) of an object.

## The application

- The application contains 3 microservices
- Each microservice takes care of only one arithmetic operation
- The microservices take inputs from the URL query form and return the result in JSON format
- The microservices are not stable and can stop serving requests. Randomly we throw errors in the code, don't modify the error logic. Rather handle the app to catch and make sure the POD is running fine.

## Services:

- `acceleration-dv` calculates `𝚫v=vf-vi`

```bash
curl http://127.0.0.1:3001/dv?vf=200&vi=5
{"dv":195}
```

- `acceleration-a` calculates `a=𝚫v/t`

```bash
curl http://127.0.0.1:3002/a?dv=200&t=5
{"a":40}
```

- `acceleration-calc` coordinates request to `acceleration-dv` and `acceleration-a` services

```bash
curl http://127.0.0.1:3000/calc?vf=200&vi=5&t=123
{"a":1.5853658536585367}
```

# Task

- Write the necessary Kubernetes deployment and service files that can be used to create the full application, running 2 instances of each microservice.
- Only `/calc` of `acceleration-calc` microservices can be available outside of the kubernetes cluster.
- Run the application on a local kubernetes cluster (Kind or Minikube or Docker for Mac) or cloud kubernetes cluster (GCP, Digital Ocean or AWS).
- Make sure the application is stable.
- Please do not change a code in services.
- **Bonus:** You can deploy to cloud of your choice (GCP or DO preferred)
- **Bonus:** You can create a CI/CD pipeline to deploy the application to the cloud.
- **Bonus:** You can create terraform files to spin up the local/cloud cluster and deploy the application.
- **Bonus:** You can use tools like Helm to reduce the boilerplate
- Your solution must work on Mac, Windows and Linux machines (Docker will help here)

# Environment Setup

- Microservices are written on Typescript and Node.js version 16.14.2
- You would need to setup `yarn`
- Run `yarn install` to setup all required components
- Run `yarn build` to build production ready code
- Run `yarn dev` to run a service in dev environment
- Run `yarn start` to run a service in production

# Instructions

- The challenge is on!
- **Send us an email with a link to repository when you finish the assesment.**
- We believe, DevOps is not about just about scripting, but about the culture of making developers productive. Impress with clear documentation of how to run it locally in your readme file.
- Also share, how much time you spend and what is the most challenging part of the challenge.
- Please complete your working solution within 7 days of receiving this challenge.
