pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: "target/surefire-reports/*.html"
                }
            }
        }

         stage ('Deploy') {
            steps {
                sh 'mvn deploy'
            }
         }
    }
}
