pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'mine', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://api-mine-302dhv-f8429e4858d21930.elb.us-east-1.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'mine', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://api-mine-302dhv-f8429e4858d21930.elb.us-east-1.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
