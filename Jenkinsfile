pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echoDependencyInstall("pip")
                clonePythonGreetings()
                displayDirectoryContent("python-greetings")
                installPipRequirements("python-greetings", "requirements.txt")
            }
        }
        stage('deploy-to-dev') {
            steps {
                echoDeployEnvironment("dev")
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
                clonePythonGreetings()
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
                clonePythonGreetings()
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
                clonePythonGreetings()
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

def echoDeployEnvironment(String envronment) {
    echo "Deploying to $environment"
}
def echoTestEnvironment(String environment) {
    echo "Testing on $environment"
}
def echoDependencyInstall(String packageManager) {
    echo "Installing $packageManager dependencies"
}
def clonePythonGreetings() {
    bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
}
def displayDirectoryContent(String directory) {
    bat "cd $directory && dir"
}
def installPipRequirements(String directoryContainingRequirements, String requirementsTextFile) {
    bat "cd $directoryContainingRequirements && pip install -r $requirementsTextFile & EXIT /B 0"
}
def stopGreetingsApp(String environment) {
    bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-$environment & EXIT /B 0"
}
def startGreetingsApp(String environment, String port) {
    bat "cd python-greetings && C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 start app.py --name greetings-app-dev -- --port 7001"
}
def cloneApiFramework() {
    bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
}
def installNpmDependencies(String appDirectory) {
    bat "cd $appDirectory && npm install"
}
def runGreetingsTests(String environment) {
    bat "cd course-js-api-framework && npm run greetings greetings_$environment"
}