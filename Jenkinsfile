pipeline {
	stage('Deploiement Ansible') {
    ansiblePlaybook (
      become: true,
      playbook: 'site.yml'
      inventory: 'inventory'
   )
}
}