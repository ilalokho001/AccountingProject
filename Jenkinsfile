pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                 withMaven(maven : 'apache-maven-3.8.4') {
                    sh 'mvn -B clean package'
                }
            }
        }

        stage('Test') {
            steps {
                 withMaven(maven : 'apache-maven-3.8.4') {
                    sh 'mvn test'
                 }
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: "target/surefire-reports/*.html"
                }
            }
        }

         stage ('Deploy') {
            steps {
                withMaven(maven : 'apache-maven-3.8.4') {
                    sh 'mvn deploy'
                }
            }
         }
    }
}
