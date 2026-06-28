pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MNK-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CE844F347550457AE00BC3DF40BECC0E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MNK-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CE844F347550457AE00BC3DF40BECC0E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
