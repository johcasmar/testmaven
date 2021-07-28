pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Sonar') { 
            steps {
                sh ('''mvn sonar:sonar \
				-Dsonar.projectKey=test \
				-Dsonar.host.url=http://35.224.61.71:9000 \
				-Dsonar.login=5e9d95f0071d41f0c0d213eb42133fdf1ece3f62
				''')
            }
        }


        stage('Front-end') {
            agent {
                docker { image 'node:14-alpine' }
            }
            steps {
                sh 'node --version'
            }
        }
    }
}
