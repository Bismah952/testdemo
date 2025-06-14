pipeline {
    agent any
    
    environment {
        // Define common environment variables here
        APP_VERSION = '1.0.0'
        BUILD_TOOL = 'maven'  // or 'gradle' depending on your project
        DEPLOY_ENV = 'production'
        NODE_VERSION = '16.14.2'  // example for Node.js projects
    }
    
    stages {
        stage('Build') {
            steps {
                echo "Building the app version ${APP_VERSION}"
                echo "Using build tool: ${BUILD_TOOL}"
                // Use bat for Windows commands instead of sh
                bat "${BUILD_TOOL} clean package -Dversion=${APP_VERSION}"
            }
        }
        
        stage('Test') {
            steps {
                echo "Running Tests with Node ${NODE_VERSION}"
                echo "Testing version ${APP_VERSION}"
                // Use bat for Windows commands
                bat "${BUILD_TOOL} test"
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying version ${APP_VERSION} to ${DEPLOY_ENV}"
                // Use bat for Windows commands
                bat "deploy-script --env ${DEPLOY_ENV} --version ${APP_VERSION}"
            }
        }
        
        stage('Master') {
            when {
                expression { params.Flag == true }
            }
            steps {
                echo "nullstring project (Version: ${APP_VERSION})"
            }
        }
        
        stage('Maps') {
            when {
                expression { params.test != null }
            }
            steps {
                echo "Running maps stage with ${BUILD_TOOL}"
            }
        }
        
        stage('Console') {
            when {
                expression { params.Flag == false }
            }
            steps {
                echo "testing project (Environment: ${DEPLOY_ENV})"
            }
        }
    }
}
