pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'clarivate.k8s.local', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://api-clarivate-k8s-local-k6kn9v-873be20c40913d9f.elb.us-east-1.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'clarivate.k8s.local', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://api-clarivate-k8s-local-k6kn9v-873be20c40913d9f.elb.us-east-1.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
