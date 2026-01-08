pipeline {
    agent { label 'mac' }

    tools {
        maven 'Maven-3.9'
        jdk 'OpenJDK-17'
    }

    environment {
        DEPLOY_DIR = "/tmp/deploy"
        TARGET_DIR = "target"
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                sh """
                mkdir -p ${DEPLOY_DIR}
                cp ${TARGET_DIR}/*.jar ${DEPLOY_DIR}/
                """
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
