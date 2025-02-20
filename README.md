## Continuous Integration and Continuous Deployment (CI/CD) with GitHub Actions

### Introduction
Welcome to this DevOps course project on Continuous Integration and Continuous Deployment (CI/CD) using GitHub Actions. This project involves setting up a simple web application (a Node.js application) and applying CI/CD practices using GitHub Actions to automate the software development process.

### Understanding CI/CD with an Analogy
Imagine you're a chef in a busy restaurant. Every dish you prepare is like a piece of software code. Without a systematic approach, you might end up with mixed-up orders, long wait times, or inconsistent food quality. A well-organized kitchen with automation (like precisely timed cooking appliances) ensures consistency and efficiency.

Similarly, CI/CD ensures that your software builds are consistently integrated, tested, and deployed with precision. Learning GitHub Actions and CI/CD helps you set up and manage an efficient 'kitchen' for software development, allowing you to deploy applications faster, with higher quality, and fewer bugs.


### Pre-requisites
Before starting this project, you should have the following:
- Basic Knowledge of Git and GitHub
    - Understanding of version control concepts.
    - Familiarity with basic Git operations (clone, commit, push, pull).
    - A GitHub account and knowledge of repository management.

- Understanding of Basic Programming Concepts
    - Preferably in JavaScript (since the example project uses Node.js).
    - Basic understanding of web applications.

- Familiarity with Node.js and npm
    - Ability to set up a simple Node.js project and install dependencies using npm.

- Text Editor or IDE
    - Visual Studio Code, Atom, Sublime Text, or any preferred editor.

- Local Development Environment
    - Node.js and npm installed on the local machine.
    - Access to the command line or terminal.

- Internet Connection
    - Stable internet connection to access GitHub and online resources.

- Basic Understanding of CI/CD Concepts (optional but helpful)
    - General awareness of Continuous Integration and Deployment.

### Lesson 1: Understanding Continuous Integration and Continuous Deployment
#### Objectives:
- Define CI/CD and understand its benefits.
- Get familiar with the CI/CD pipeline.

#### Overview:
- Continuous Integration (CI): Merging all developers' working copies to a shared mainline several times a day.
- Continuous Deployment (CD): Automatically and reliably releasing software changes to production.
- Benefits: Faster releases, improved productivity, better code quality, and enhanced customer satisfaction.
- CI/CD Pipeline:
    - Version control (Git, GitHub)
    - Code integration and automated testing
    - Application build and deployment
- Tools: GitHub Actions, testing frameworks, deployment tools.

### Lesson 2: Introduction to GitHub Actions
#### Objectives:
- Understand what GitHub Actions is.
- Learn key concepts and terminology.

#### Key Concepts:
- Workflow: A YAML-defined automated process consisting of jobs.
- Event: Triggers workflows (e.g., push, pull request, scheduled time).
- Job: A set of steps executed on the same runner.
- Step: Individual tasks running commands.
- Action: Standalone commands combined into steps.
- Runner: A server executing workflows (GitHub-hosted or self-hosted).

#### Practical Implementation
- Setting Up the Project

1. Initialize a GitHub Repository
    - Create a new repository on GitHub.
    - Clone it to your local machine.

2. Create a Simple Node.js Application
    ```sh
    const express = require('express');
    const app = express();
    const port = process.env.PORT || 3000;

    app.get('/', (req, res) => {
    res.send('Hello World!');
    });

    app.listen(port= 4000, () => {
    console.log(`App listening at http://localhost:${port}`);
    });
    ```

    - Push the code to GitHub.

#### Writing Your First GitHub Action Workflow
1. Create a Workflow File
    - Create .github/workflows/node.js.yml.

2. Define the Workflow
    ```sh
        # Name of the workflow
        name: Node.js CI

        # Specifies when the workflow should be triggered
        on:
            # Triggers the workflow on 'push' events to the 'main' branch
            push:
                branches: [ main ]

            # Also triggers the workflow on 'pull_request' events targeting the 'main' branch
            pull_request:
                branches: [ main ]

        # Defines the jobs that the workflow will execute
        jobs:
            # Job identifier, can be any name (here it's 'build')
            build:
                # Specifies the type of virtual host environment (runner) to use
                runs-on: ubuntu-latest

                # Steps represent a sequence of tasks that will be executed as part of the job
                steps:
                # Checks-out your repository under $GITHUB_WORKSPACE, so the job can access it
                - name: Checkout repository
                    uses: actions/checkout@v2

                # Sets up the specified version of Node.js
                - name: Set up Node.js
                    uses: actions/setup-node@v1
                    with:
                    node-version: 12

                - name: Install dependencies
                    run: npm i

                - name: Build project
                    run: npm run build
    ```

#### Explanation:
- Triggers on: Push and pull request events on the main branch.
- Runs on: Ubuntu virtual machine.
- Steps:
    - Checkout repository.
    - Setup Node.js (version 12).
    - Install dependencies using npm ci.
    - Run tests using npm test.
    - Build the project using npm run build.


## Conclusion
This project introduces CI/CD with GitHub Actions, helping automate testing and deployment of a simple Node.js application. Mastering these concepts ensures efficient software development workflows, reducing errors and increasing deployment speed.