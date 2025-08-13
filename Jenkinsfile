pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'clvhyd.k8s.local', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://api-clvhyd-k8s-local-ig0m27-9523f4d3c4ca2762.elb.us-east-1.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'clvhyd.k8s.local', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://api-clvhyd-k8s-local-ig0m27-9523f4d3c4ca2762.elb.us-east-1.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
