pipeline {
    agent any

    stages {
        stage('Build and Test') {
            steps {
                    sh 'npm install'                  
                    sh './node_modules/.bin/eslint -f checkstyle --ignore-path .gitignore . --fix > eslint.xml'
                    sh './node_modules/.bin/nyc node_modules/.bin/_mocha "test/**/*.js" > coverage.xml'
                    sh 'ls-ls output'
                  
        
            }
        }
        stage('Checkstyle') {
           steps {        
        checkstyle pattern: 'eslint.xml'
           }
        }
       
         stage ("Extract test results") {
             steps {
    cobertura coberturaReportFile: 'coverage.xml'
                              }
         }
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
} 
