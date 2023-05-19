pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echoDependencyInstall("pip")
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                displayDirectoryContent("python-greetings")
                bat "cd python-greetings && pip install -r requirements.txt & EXIT /B 0"
            }
        }
        stage('deploy-to-dev') {
            steps {
                echoDeployEnvironment("dev")
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-dev & EXIT /B 0"
                startGreetingsApp("dev", "7001")
            }
        }
        stage('tests-on-dev') {
            steps {
                echoTestEnvironment("dev")
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("dev")
            }
        }
        stage('deploy-to-staging') {
            steps {
                echoDeployEnvironment("staging")
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-staaging & EXIT /B 0"
                startGreetingsApp("staging", "7002")
            }
        }
        stage('tests-on-staging') {
            steps {
                echoTestEnvironment("staging")
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"()
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("staging")
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echoDeployEnvironment("preprod")
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-preprod & EXIT /B 0"
                startGreetingsApp("preprod", "7003")
            }
        }
        stage('tests-on-preprod') {
            steps {
                echoTestEnvironment("preprod")
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"()
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("preprod")
            }
        }
        stage('deploy-to-prod') {
            steps {
                echoDeployEnvironment("prod")
                bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
                bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-prod & EXIT /B 0"
                startGreetingsApp("prod", "7004")
            }
        }
        stage('tests-on-prod') {
            steps {
                echoTestEnvironment("prod")
                bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"()
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("prod")
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

/* EXIT /B0 nestrādā no metodes izsaukuma
def clonePythonGreetings() {
    bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
}
*/

def displayDirectoryContent(String directory) {
    bat "cd $directory && dir"
}
/* EXIT /B0 nestrādā no metodes izsaukuma
def installPipRequirements(String directoryContainingRequirements, String requirementsTextFile) {
    bat "cd $directoryContainingRequirements && pip install -r $requirementsTextFile & EXIT /B 0"
}
*/
/* EXIT /B0 nestrādā no metodes izsaukuma
def stopGreetingsApp(String environment) {
    bat "C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 delete greetings-app-$environment & EXIT /B 0"
}
*/
def startGreetingsApp(String environment, String port) {
    bat "cd python-greetings && C:\\Users\\Zenith\\AppData\\Roaming\\npm\\pm2 start app.py --name greetings-app-dev -- --port 7001"
}
/* EXIT /B0 nestrādā no metodes izsaukuma
def cloneApiFramework() {
    bat "git clone https://github.com/mtararujs/course-js-api-framework & EXIT /B 0"
}
*/
def installNpmDependencies(String appDirectory) {
    bat "cd $appDirectory && npm install"
}
def runGreetingsTests(String environment) {
    bat "cd course-js-api-framework && npm run greetings greetings_$environment"
}










