pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webapps', serverUrl: 'https://139C09D4B7F530C98ED3AFD24454EF7D.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes-admin@kubernetes', contextName: '', credentialsId: 'k8-token-micro', namespace: 'webapps', serverUrl: 'https://139C09D4B7F530C98ED3AFD24454EF7D.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
