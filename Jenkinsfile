pipeline {
    agent {
        label 'devops'
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
                dir('tomcat') {
                    sh 'ls'
                    //sh 'terraform apply -auto-approve'
                }
            }
        }
        
        stage('Ansible Playbook') {
            steps {
                dir('ubuntu') {
                    //sh 'ansible-playbook your-playbook.yml'
		                sh 'ls'
                }
            }
        }
    }
}
