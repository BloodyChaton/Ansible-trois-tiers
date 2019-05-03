pipeline {
	agent any
	stages {
stage('Deploy to test'){
    steps {
    	    git credentialsId: '9cbaca88-64ed-4179-b704-ccf7e98d87e1', url: 'https://github.com/BloodyChaton/demomaven.git', branch: 'features/Luc_ansible_jenkins'
            echo 'Deploying to test'
            sh 'ansible-playbook -i inventory site.yml'
    }
}
    }
}