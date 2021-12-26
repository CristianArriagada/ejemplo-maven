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
                sh "./mvnw clean compile -e"              
                }
            }
        }
        stage("Test Code"){
            steps {
                script {
                sh "echo 'Test Code!'"
                sh "./mvnw clean test -e"
                }
            }
        }
        stage("Jar Code"){
            steps {
                script {
                sh "echo 'Build .Jar!'"
                sh "./mvnw clean package -e"
                }
            }
        }
        stage("Run jar"){
            steps {
                script {
                sh "echo 'Run .Jar!'"
                sh "nohup bash mvnw spring-boot:run &"
                }
            }
        }
        stage("testing app"){
            steps {
                script {
                sh "echo 'Testing APP!'"
                sh "curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'"
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