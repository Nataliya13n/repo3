pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
    stage('Test') {
        steps {
            echo 'Testing..'
                sh 'mvn test'
        }
    }
        post {
            always {
                echo 'Allure report generate'
                generateAllure()
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

def generateAllure() {
    allure([
            includeProperties: true,
            jdk              : '',
            properties       : [],
            reportBuildPolicy: 'ALWAYS',
            results          : [[path: 'target/allure-results']]
    ])
}
