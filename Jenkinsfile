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
                clonePythonGreetings()
                stopGreetingsApp("dev")
                startGreetingsApp("dev", "7001")
            }
        }
        stage('tests-on-dev') {
            steps {
                echoTestEnvironment("dev")
                cloneApiFramework()
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("dev")
            }
        }
        stage('deploy-to-staging') {
            steps {
                echoDeployEnvironment("staging")
                clonePythonGreetings()
                stopGreetingsApp("staging")
                startGreetingsApp("staging", "7002")
            }
        }
        stage('tests-on-staging') {
            steps {
                echoTestEnvironment("staging")
                cloneApiFramework()
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("staging")
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echoDeployEnvironment("preprod")
                clonePythonGreetings()
                stopGreetingsApp("preprod")
                startGreetingsApp("preprod", "7003")
            }
        }
        stage('tests-on-preprod') {
            steps {
                echoTestEnvironment("preprod")
                cloneApiFramework()
                installNpmDependencies("course-js-api-framework")
                runGreetingsTests("preprod")
            }
        }
        stage('deploy-to-prod') {
            steps {
                echoDeployEnvironment("prod")
                clonePythonGreetings()
                stopGreetingsApp("prod")
                startGreetingsApp("prod", "7004")
            }
        }
        stage('tests-on-prod') {
            steps {
                echoTestEnvironment("prod")
                cloneApiFramework()
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
def clonePythonGreetings() {
    bat "git clone https://github.com/mtararujs/python-greetings & EXIT /B 0"
}
def displayDirectoryContent(String directory) {
    bat "cd $directory && dir"
}
def installPipRequirements(String directoryContainingRequirements, String requirementsTextFile) {
    bat "cd $directoryContainingRequirements && pip install -r $requirementsTextFile"
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










