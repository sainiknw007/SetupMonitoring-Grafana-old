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

	stage('Copy pem file to tomcat directory') {
            steps {
                sh 'cp /home/ubuntu/hostdrive/tomcat/monitor.pem tomcat/'
            }
        }
        stage('Create Infra') {
            steps {
                dir('ubuntu') {
                    //sh 'terraform init'
		    //sh 'terraform validate'
		    //sh 'terraform plan'
                    //sh 'terraform apply -auto-approve' 
		    sh 'ls'
                }
            }
        }
        
        stage('Install Tomcat') {
            steps {
                dir('tomcat') {
                    //sh 'ansible-playbook -i ec2.py playbook/tomcatdemo.yml'
		    sh 'ls'
                }
            }
        }

	stage('Install NodeExporter') {
            steps {
                dir('tomcat') {
                    //sh 'ansible-playbook -i ec2.py playbook/node_exporter.yml'		    
                }
            }
        }

	stage('Install Prometheus') {
            steps {
                dir('tomcat') {
                    //sh 'ansible-playbook -i ec2.py playbook/prometheus.yml'
                }
            }
        }

	stage('Install Grafana') {
            steps {
                dir('tomcat') {
                    //sh 'ansible-playbook -i ec2.py playbook/grafana.yml'
                }
            }
        }
    }
}
