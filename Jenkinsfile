pipeline {
    agent any

    stages {
        stage('deploy to k8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://71B224FE2F6864503442C7F57F5F51A8.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        stage('verify deployment') {
            steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://71B224FE2F6864503442C7F57F5F51A8.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl get all -n webapps"           
                }
            }
        }
    }
}
