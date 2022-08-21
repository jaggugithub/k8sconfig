pipeline {
    agent any
    stages {
        stage('Configure k8s and Docker Packages on both Master & Worker nodes') {
            steps {
                ansiblePlaybook credentialsId: 'k8scluster-key', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'aws_ec2.yaml', playbook: 'packages.yaml'
            }
        }
        stage('Configure k8s_cluster_master') {
            steps {
                ansiblePlaybook credentialsId: 'k8scluster-key', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'aws_ec2.yaml', playbook: 'masternodes.yaml'
            }
        }
        stage('Configure k8s_cluster_worker') {
            steps {
                ansiblePlaybook credentialsId: 'k8scluster-key', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'aws_ec2.yaml', playbook: 'workernodes.yaml'
            }
        }
    }
} 