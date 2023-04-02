pipeline {
    agent {
        docker {
            image 'maven:3.8.3-openjdk-17-slim'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}

def githubUrl = 'https://github.com/fdzamtovski/IKTRepo.git'
def githubCredentialsId = '84224515-a610-4532-9591-e7cb91709d03'

