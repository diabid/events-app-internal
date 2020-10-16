pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Retrieving source from github' 
                git branch: 'master',
                    url: 'https://github.com/diabid/events-app-internal.git'
                echo 'Did we get the source?' 
                sh 'ls -a'
            }
        }
        stage('Stage 2') {
            steps {
                echo 'workspace and versions' 
                sh 'echo $WORKSPACE'
                sh 'docker --version'
                sh 'gcloud version'
                sh 'nodejs -v'
                sh 'npm -v'
        
            }
        }        
         stage('Stage 3') {
            environment {
                PORT = 8085
            }
            steps {
                echo 'install dependencies' 
                sh 'npm install'
                echo 'Run tests'
                sh 'npm test'
        
            }
        }        
         stage('Stage 4') {
            steps {
                echo "build id = ${env.BUILD_ID}"
                echo 'Tests passed on to build Docker container'
            }
        }        
         stage('Stage 5') {
            steps {
                echo 'Starting App'
                sh 'npm start'
            }
        }        
               

        
    }
}
