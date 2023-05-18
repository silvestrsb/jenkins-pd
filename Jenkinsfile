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
                bat "cd python-greetings && C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 start app.py --name greetings-app-dev -- --port 7001"
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'Testing on dev'
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
                bat "cd course-js-api-framework && npm install"
                bat "cd course-js-api-framework && npm run greetings greetings_dev"
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'Deploying to staging'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-staging & EXIT /B 0"
                bat "cd python-greetings && C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 start app.py --name greetings-app-staging -- --port 7002"
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'Testing on staging'
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
                bat "cd course-js-api-framework && npm install"
                bat "cd course-js-api-framework && npm run greetings greetings_staging"
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'Deploying to preprod'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-preprod & EXIT /B 0"
                bat "cd python-greetings && C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 start app.py --name greetings-app-preprod -- --port 7003"
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'Testing on preprod'
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
                bat "cd course-js-api-framework && npm install"
                bat "cd course-js-api-framework && npm run greetings greetings_preprod"
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'Deploying to prod'
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-prod & EXIT /B 0"
                bat "cd python-greetings && C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 start app.py --name greetings-app-prod -- --port 7004"
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'Testing on prod'
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
                bat "cd course-js-api-framework && npm install"
                bat "cd course-js-api-framework && npm run greetings greetings_prod"
            }
        }
    }
}
