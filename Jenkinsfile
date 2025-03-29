pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/yourusername/multi-cloud-dr.git'
            }
        }

        stage('Deploy to AWS') {
            steps {
                ansiblePlaybook(
                    playbook: 'deploy.yml',
                    inventory: 'inventory.ini',
                    extras: '--extra-vars "target_host=aws"'
                )
            }
        }

        stage('Deploy to Azure') {
            steps {
                ansiblePlaybook(
                    playbook: 'deploy.yml',
                    inventory: 'inventory.ini',
                    extras: '--extra-vars "target_host=azure"'
                )
            }
        }
    }
}
