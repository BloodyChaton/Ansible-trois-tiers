pipeline {
	agent vagrant
	stages {
stage('Deploy to test'){
    steps {
        dir(/home/user01/ansible/Ansible-trois-tiers/){
            echo 'Deploying to test'
            sh 'ansible-playbook -i inventory site.yml'
        }
    }
}
    }
}