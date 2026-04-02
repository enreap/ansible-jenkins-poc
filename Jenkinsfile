pipeline {
    agent any

    stages {
        stage('Run Ansible Playbook') {
            steps {
                sshagent(['ansible-server-key']) {
                    sh '''
                    ssh ansible@<ansible-master-ip> "
                    ansible-playbook -i /home/ansible/hosts.ini /home/ansible/deploy.yml
                    "
                    '''
                }
            }
        }
    }
}
