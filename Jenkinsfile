pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webapps', serverUrl: 'https://B932E82E52F9B557A9F65E67A0924560.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webapps', serverUrl: 'https://B932E82E52F9B557A9F65E67A0924560.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
