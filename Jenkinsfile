pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'sagaramd', toolName: 'docker') {
                        sh "docker build -t sagaramd/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push sagaramd/adservice:latest "
                    }
                }
            }
        }
    }
}
