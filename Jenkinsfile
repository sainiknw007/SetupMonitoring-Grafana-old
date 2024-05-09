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
        
        stage('Create Infra') {
            steps {
                dir('ubuntu') {
                    sh 'terraform init'
		    sh 'terraform validate'
		    sh 'terraform plan'
                    sh 'terraform apply -auto-approve'                    
                }
            }
        }
        
        stage('Install Tomcat') {
            steps {
                dir('ubuntu') {
                    sh 'ansible-playbook -i ec2.py playbook/tomcatdemo.yml'
                }
            }
        }

	stage('Install NodeExporter') {
            steps {
                dir('ubuntu') {
                    sh 'ansible-playbook -i ec2.py playbook/node_exporter.yml'
                }
            }
        }

	stage('Install Prometheus') {
            steps {
                dir('ubuntu') {
                    sh 'ansible-playbook -i ec2.py playbook/prometheus.yml'
                }
            }
        }

	stage('Install Prometheus') {
            steps {
                dir('ubuntu') {
                    sh 'ansible-playbook -i ec2.py playbook/grafana.yml'
                }
            }
        }
    }
}
