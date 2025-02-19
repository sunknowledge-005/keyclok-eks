pipeline {
    agent{label 'dev'}
    
    environment {
        KUBECTL = "/usr/local/bin/kubectl"  // Define the variable here
    }

    stages {
        
        stage("checkout"){
            steps{
                git url: 'https://github.com/sunknowledge-005/keyclok-eks.git', branch: 'main'
            }
        }
        stage('Hello') {
            steps {
                 sh "${KUBECTL} apply -f  a.yml"
                 sh "${KUBECTL}  apply -f  svc.yml"
                // sh "sudo -u ubuntu kubectl get node"
                
            }
        }
    }
}
