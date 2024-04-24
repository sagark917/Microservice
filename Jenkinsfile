pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token', namespace: 'webappsmicro', serverUrl: 'https://192.168.100.14:6443']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token', namespace: 'webappsmicro', serverUrl: 'https://192.168.100.14:6443']]) {
                    sh "kubectl get svc -n webappsmicro"
                }
            }
        }
    }
}
