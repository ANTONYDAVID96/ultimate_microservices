pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my20-cluster', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://239D9335EB04F02BCE06BF34D3B55860.gr7.us-east-1.eks.amazonaws.co') {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my20-cluster', contextName: '', credentialsId: 'k8s-cred', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://239D9335EB04F02BCE06BF34D3B55860.gr7.us-east-1.eks.amazonaws.co') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
