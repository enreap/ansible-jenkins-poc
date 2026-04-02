pipeline {
    agent any

    environment {
        ANSIBLE_KEY = 'ansible-key'          // SSH credential in Jenkins
        INVENTORY = 'ansible/hosts.ini'
        PLAYBOOK = 'ansible/playbooks/deploy.yml'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:your-repo/ansible-poc.git'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sshagent([ANSIBLE_KEY]) {
                    sh "ansible-playbook -i ${INVENTORY} ${PLAYBOOK} -u ec2-user"
                }
            }
        }
    }
}
