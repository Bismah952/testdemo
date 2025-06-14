pipeline {
    agent any
    
    environment {
        FOR_VERSION = "13.10"
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building project'
                echo "Building version ${FOR_VERSION}"
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running Tests'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the app'
            }
        }
        
        stage('Master') {
            when {
                expression { params.Flag == true }
            }
            steps {
                echo "nullstring project"
            }
        }
        
        stage('Maps') {
            when {
                expression { params.test != null }
            }
            steps {
                echo "Running maps stage"
            }
        }
        
        stage('Console') {
            when {
                expression { params.Flag == false }
            }
            steps {
                echo "testing project"
            }
        }
    }
}
