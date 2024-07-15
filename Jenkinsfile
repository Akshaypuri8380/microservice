pipeline {
    agent any

    stages {
        stage('deploy kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://834BCE5EC0E4CA0950ADD46227154EA2.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f  deployment-service.yml"
                     
                }
           }
        }
        
        stage('verify deployement') {
            steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://834BCE5EC0E4CA0950ADD46227154EA2.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                 }
            }     
        }
    }
}  
