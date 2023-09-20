# React.js Deployment CI/CD

This repository contains a GitHub Actions workflow for automating the deployment of a React.js application using Continuous Integration and Continuous Deployment (CI/CD) pipelines. This setup allows you to automatically build and deploy your React.js application whenever changes are pushed to the `main` branch.

## Prerequisites

Before setting up this CI/CD workflow, make sure you have the following prerequisites in place:

1. Your React.js application code hosted on a GitHub repository.
2. Access to a remote server where you want to deploy the React.js application.
3. Node.js version 12 or higher installed on the remote server.
4. Nginx installed on the server.
5. SSH access to the remote server.

## Workflow Setup

To set up the CI/CD workflow for your React.js application, follow these steps:

1. **Copy the CI/CD Configuration**:

   Copy the provided CI/CD configuration code and create a file named `.github/workflows/main.yml` in the root of your GitHub repository. Paste the copied code into this file.

2. **Configure the Main Branch**:

   In the workflow configuration file, ensure that the `branches` under `on` matches your main branch name. By default, it is set to `main`.

3. **Node.js Version**:

   You can change the Node.js version by modifying the `node-version` field under the `Setup Node.js` step. Make sure it matches your desired Node.js version.

4. **Deployment Path**:

   Update the `remote_path` under the `rsync deployments` step to specify the path on your deployment server where you want to deploy the React.js application. In the provided example, it deploys to `/var/www/html/build`, but you can change it according to your server's setup.

## Workflow Explanation

Here's a brief explanation of what each step in the CI/CD workflow does:

1. **Checkout code**: This step checks out your project's code from the repository.

2. **Setup Node.js**: It sets up the specified Node.js version for building the React.js application.

3. **Install dependencies and build**: This step installs the project dependencies and builds the React.js application. It also sets environment variables using the GitHub secrets.

4. **rsync deployments**: Finally, it uses `rsync` to deploy the built application to the specified remote server path, using the SSH credentials provided in the GitHub secrets.

## Usage

Once you have set up the workflow and pushed changes to the `main` branch, GitHub Actions will automatically trigger the workflow. You can monitor the progress and check for any deployment issues in the Actions tab of your GitHub repository.

With this CI/CD setup, your React.js application will be automatically built and deployed to your server whenever you make changes to the `main` branch, streamlining your development and deployment process.
