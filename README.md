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
