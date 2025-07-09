pipeline {
    agent any

    stages {
        stage('Validate IaC') {
            steps {
                sh 'vagrant validate'
                sh 'ansible-lint jenkins.yml'
            }
        }
        stage('Deploy Infrastructure') {
            steps {
                sh 'vagrant up'
            }
        }
    }

    post {
        failure {
            echo 'Deployment failed. Rollback or alert here.'
        }
    }
}
