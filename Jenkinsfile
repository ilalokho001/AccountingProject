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
                sh 'mvn surefire-report:report'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: "target/site/*.html"
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
