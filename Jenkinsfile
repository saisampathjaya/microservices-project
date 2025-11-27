pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'My-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B043883E76BD3F195DF30EF5CEFE0A38.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'My-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B043883E76BD3F195DF30EF5CEFE0A38.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
