pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'cd demo-app && mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'cd demo-app && mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'cd demo-app && mvn package'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                mkdir -p /tmp/deploy
                cp demo-app/target/*.jar /tmp/deploy/
                '''
            }
        }
    }
}
