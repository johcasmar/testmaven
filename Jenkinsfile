pipeline {
    agent any
    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Sonar') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            } 
            steps {
                sh ('''mvn sonar:sonar \
				-Dsonar.projectKey=bbva \
				-Dsonar.host.url=http://192.168.20.33:9000 \
				-Dsonar.login=da062c153d28f8a8336eb06ed0e30a6979d716af
				''')
            }
        }


        
    }
}
