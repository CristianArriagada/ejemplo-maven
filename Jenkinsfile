import groovy.json.JsonSlurperClassic

def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}
pipeline {
    agent any
    stages {

        stage("Compile Code"){
            steps {
                script {
                sh "echo 'Compile Code!'"
                ./mvnw clean compile -e
                }
            }
        }
        stage("Test Code"){
            steps {
                script {
                sh "echo 'Test Code!'"
                ./mvnw clean test -e
                }
            }
        }
        stage("Jar Code"){
            steps {
                script {
                sh "echo 'Build .Jar!'"
                ./mvnw clean package -e
                }
            }
        }
    }
    post {
        always {
            sh "echo 'fase always executed post'"
        }
        success {
            sh "echo 'fase success'"
        }

        failure {
            sh "echo 'fase failure'"
        }
    }
}