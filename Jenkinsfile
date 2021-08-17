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
			  -Dsonar.host.url=http://192.168.39.113:9000 \
			  -Dsonar.login=16471f9e1ed8b54fde00dd776782fd5eaa66d4e6
				''')
            }
        }


        
    }
}
