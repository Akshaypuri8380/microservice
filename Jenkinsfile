pipeline { 
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    withKubeCredentials(
                        credentialsId: 'k8-token', 
                        serverUrl: 'https://834BCE5EC0E4CA0950ADD46227154EA2.gr7.ap-south-1.eks.amazonaws.com'
                    ) {
                        sh "kubectl apply -f deployment-service.yml -n webapps"
                        sleep time: 60, unit: 'SECONDS'
                    }
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                script {
                    withKubeCredentials(
                        credentialsId: 'k8-token', 
                        serverUrl: 'https://834BCE5EC0E4CA0950ADD46227154EA2.gr7.ap-south-1.eks.amazonaws.com'
                    ) {
                        sh "kubectl get all -n webapps"
                    }
                }
            }
        }
    }
}
