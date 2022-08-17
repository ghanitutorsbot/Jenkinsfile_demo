pipeline {
    agent any

    stages {
        stage('code') {
            steps {
                git credentialsId: '4f2c41b1-86df-43ac-8c49-a5df0f41a82a', url: 'https://github.com/ghanitutorsbot/maven_demo.git'
            }
        }
         stage('build') {
            steps {
                bat 'mvn verify'
            }
        }
           stage('SAST') {
            steps {
                bat 'mvn sonar:sonar'
            }
        }
              stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '752d6505-a033-4979-869c-5ec7d1312eb3', path: '', url: 'http://localhost:8081/')], contextPath: 'declarativewar', war: '**/*.war'
            }
        }
    }
}
