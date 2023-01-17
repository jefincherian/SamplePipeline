pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                withMaven(maven : 'apache-maven-3.8.5'){
                    bat 'mvn clean compile'
                }
            }
        }

        stage('Test') {
            steps {
                withMaven(maven : 'apache-maven-3.8.5'){
                 bat 'mvn clean test'
                }
             }
        }

        stage('Deploy') {
            steps {
                echo 'Hello World - Deploy'
            }
        }
    }
        post{
            always{
                mail to: "jefin@qburst.com",
                subject: "Jenkins Build:${currentBuild.currentResult}: ${env.JOB_NAME}",
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}\n\nThanks!\nAutomation Team"
                //attachLog: true
            }
        }
}
