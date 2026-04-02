pipeline {
    agent any

    environment {
        ANSIBLE_KEY = 'jenkins-ssh-ubuntu'          // SSH credential in Jenkins
        INVENTORY = 'hosts.ini'
        PLAYBOOK = 'deploy.yml'
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
                    sh "ssh ubuntu@13.113.78.20 'ansible-playbook -i ${env.INVENTORY} ${env.PLAYBOOK}'"
                }
            }
        }
    }
}
