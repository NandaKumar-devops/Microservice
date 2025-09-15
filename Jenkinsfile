pipeline {
    agent any

    stages {
        stage('Deploy To kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKSMicro-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://189C0081F009318487BAD762543A5632.gr7.us-east-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                
               }
            }
        }
        stage('verify Deployment'){
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKSMicro-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://189C0081F009318487BAD762543A5632.gr7.us-east-1.eks.amazonaws.com']]) {
               sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
