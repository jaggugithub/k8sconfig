pipeline {
    agent any
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jaggugithub/k8sconfig.git'
            }
        }
        stage('Configure k8s_cluster_Master') {
            steps {
                ansiblePlaybook credentialsId: 'WebappServers', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'aws_ec2.yaml', playbook: 'masternode.yaml'
            }
        }
        stage('Configure k8s_cluster_worker1') {
            steps {
                ansiblePlaybook credentialsId: 'WebappServers', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'aws_ec2.yaml', playbook: 'worker1.yaml'
            }
        }
        stage('Configure k8s_cluster_worker2') {
            steps {
                ansiblePlaybook credentialsId: 'WebappServers', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'aws_ec2.yaml', playbook: 'worker2.yaml'
            }
        }
    } 