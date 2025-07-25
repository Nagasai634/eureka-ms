pipeline {
    agent {
        label 'jenkins-slave1'
    }
    tools {
        jdk 'jdk'
        maven 'maven'
    }
    environment {
        APPLICATION_NAME = 'eureka'
        SONAR_URL = 'http://34.122.117.31:9000'
        SONAR_TOKEN = credetinals('sonar_creds')
    }
    stages {
        stage('build') {
            steps{
                echo "Building ${APPLICATION_NAME}"
                sh "mvn clean package -DskipTests=true"
            }
        }
        stage('codequality') {
            steps {
                echo "scanning ${APPLICATION_NAME} code"
                sh """
                mvn clean verify sonar:sonar \
                      -Dsonar.projectKey=eureka-ms \
                      -Dsonar.host.url=${SONAR_URL} \
                      -Dsonar.login=${SONAR_TOKEN}
                """
            }
        }
    }
}