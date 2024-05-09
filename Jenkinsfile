pipeline {
    agent {
        label 'monitor'
    }
    tools {
        // Specify the Git installation by name
        git 'Git'
    }
    stages {
        stage('git version') {
            steps {
                sh 'git --version'
            }
        }	    
    
        stage('Checkout') {
            steps {
                checkout scm
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
