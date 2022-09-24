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
// If you want to clean the workspace for this pipeline job please uncomment the post stages section(**BUT NOT THIS LINE**).
    // post {
	// 	always {
    //         cleanWs()   // This is to clean the workspace for this job
	//     }
 	// }
} 