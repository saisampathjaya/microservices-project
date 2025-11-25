pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'My-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://11987AE7A96FC4532CC91C479AAF8606.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'My-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://11987AE7A96FC4532CC91C479AAF8606.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
