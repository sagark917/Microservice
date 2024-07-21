pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webapps', serverUrl: 'https://E0E49FEA391EBDF99FE183AC9CE902AC.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webapps', serverUrl: 'https://E0E49FEA391EBDF99FE183AC9CE902AC.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
