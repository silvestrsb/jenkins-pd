pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echo 'Installing pip dependencies'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "cd python-greetings && dir"
                bat "cd python-greetings && pip install -r requirements.txt"
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo 'Deploying to dev'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-dev & EXIT /B 0"
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'Testing on dev'
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'Deploying to staging'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'Testing on staging'
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'Deploying to preprod'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'Testing on preprod'
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'Deploying to prod'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'Testing on prod'
            }
        }
    }
}
