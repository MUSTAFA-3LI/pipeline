pipeline {
    agent any 

    stages {
        stage('Requirements') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        

        stage('Docker Login') {
            steps {
                withCredentials([string(credentialsId: 'JENKINS_PASSWORD', variable: 'DOCKER_PASSWORD')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u mustafa3li --password-stdin'
                }
            }
        }

        stage('Docker Build') { 
            steps {
                sh 'docker build -t mustafa3li/palestine:latest .' 
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push mustafa3li/palestine:latest'
            }
        }
    }
}