# Learn Jenkins Pipeline

This repository contains a collection of Jenkins Pipeline examples and tutorials to help you learn how to use Jenkins for continuous integration and continuous deployment (CI/CD).

## Jenkinsfile

The `Jenkinsfile` is a text file that contains the definition of a Jenkins Pipeline. It can be written in either Declarative or Scripted syntax. Below is an example of a simple Declarative Pipeline:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
```

## Agent Labels

Agent labels are used to specify which Jenkins agent (node) should run the pipeline stages. You can define an agent at the top level of the pipeline or within individual stages. Here’s an example of using an agent label:

```groovy
pipeline {
    agent { label 'linux' }

    stages {
        stage('Build') {
            steps {
                echo 'Building on Linux agent...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing on Linux agent...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying from Linux agent...'
            }
        }
    }
}
```

## Post

The `post` section allows you to define actions that should be executed after the pipeline stages have completed, regardless of whether they succeeded or failed. Here’s an example:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages.'
        }
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails.'
        }
        cleanup {
            echo 'This will run after the pipeline completes, regardless of success or failure.'
        }
    }
}
```

## Stages

Stages are used to organize the pipeline into distinct phases, such as build, test, and deploy. Each stage can contain multiple steps that define the actions to be performed. Here’s an example of a pipeline with multiple stages:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
```

## Steps

Steps are the individual tasks that are executed within a stage. They can include shell commands, scripts, or built-in Jenkins functions. Here’s an example of using steps in a pipeline:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                echo 'Compiling source code...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running unit tests...'
                echo 'Checking code quality...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to production...'
                echo 'Notifying stakeholders...'
            }
        }
    }
}
```
