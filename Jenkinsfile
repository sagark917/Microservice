pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webappsmicro', serverUrl: 'https://3.109.208.46:6443']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webappsmicro', serverUrl: 'https://3.109.208.46:6443']]) {
                    sh "kubectl get svc -n webappsmicro"
                }
            }
        }
    }
}
