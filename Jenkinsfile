pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/takneekigyanguru/SetupMonitor.git'
            }
        }
        
        stage('Terraform Apply') {
            steps {
                dir('terraform') {
                    sh 'ls'
                    //sh 'terraform apply -auto-approve'
                }
            }
        }
        
        stage('Ansible Playbook') {
            steps {
                dir('ansible') {
                    //sh 'ansible-playbook your-playbook.yml'
		                sh 'ls'
                }
            }
        }
    }
}
