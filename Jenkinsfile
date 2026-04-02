pipeline {
    agent any

    environment {
        ANSIBLE_KEY = 'jenkins-ssh-ubuntu'          // SSH credential in Jenkins
        INVENTORY = 'hosts.ini'
        PLAYBOOK = 'deploy.yaml'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/enreap/ansible-jenkins-poc.git'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sshagent([env.ANSIBLE_KEY]) {
                    sh """
                    scp -o StrictHostKeyChecking=no ${env.INVENTORY} ubuntu@13.113.78.20:~/ && \
                    scp -o StrictHostKeyChecking=no ${env.PLAYBOOK} ubuntu@13.113.78.20:~/ && \
                    ssh -o StrictHostKeyChecking=no ubuntu@13.113.78.20 \"ansible-playbook -i ~/hosts.ini ~/deploy.yaml\"
                    """
                }
            }
        }
    }
}
