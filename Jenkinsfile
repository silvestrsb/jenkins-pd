pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World - Jenkins PD'
            }
        }
        stage('Check node version') {
            steps {
                bat "node --version"
            }
        }
    }
}
