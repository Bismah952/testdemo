pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the app'
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
