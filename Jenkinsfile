pipeline {
	agent any
	stages {
stage('Deploy to test'){
    steps {
            echo 'Deploying to test'
            sh 'ansible-playbook -i inventory site.yml'
    }
}
    }
}