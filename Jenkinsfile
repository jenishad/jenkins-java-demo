pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar'
            junit 'target/surefire-reports/*.xml'
        }

        success {
            echo 'BUILD SUCCESSFUL'
        }

        failure {
            echo 'BUILD FAILED'
        }
    }
}
