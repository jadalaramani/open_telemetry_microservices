pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                   withKubeConfig(caCertificate: '', clusterName: 'my-cluster', contextName: '', credentialsId: 'k8s-cred', namespace: 'ms', restrictKubeConfigAccess: false, serverUrl: 'https://D05DA7ACCADC529A3D17B80C7BA6D796.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                  withKubeConfig(caCertificate: '', clusterName: 'my-cluster', contextName: '', credentialsId: 'k8s-cred', namespace: 'ms', restrictKubeConfigAccess: false, serverUrl: 'https://D05DA7ACCADC529A3D17B80C7BA6D796.gr7.us-east-1.eks.amazonaws.com') {  
                  sh "kubectl get svc -n ms"
                }
            }
        }
    }
}
