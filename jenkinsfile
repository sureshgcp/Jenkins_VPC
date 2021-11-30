pipeline {
	agent any 
  stages {  
		stage('VPC Network with Automode') {
			steps {
				sh 'gcloud compute networks create nasa-vpc-auto --description="VPC with Automode"   --subnet-mode=auto --quiet'
				  }
				}
		stage('VPC Network with Custom') {
			steps {
				sh 'gcloud compute networks create nasa-vpc-manual --description="VPC with Custom"   --subnet-mode=custom --quiet'
				  }
				}

		stage('SUBNET create') {
			steps {
				sh 'gcloud compute networks subnets create nasa-vpc-manual-subnet --network=nasa-vpc-manual --range=10.10.0.0/16 --region=us-central1'
				  }
				}
				
				stage('VPC List ') {
			steps {
				sh 'gcloud compute networks list'
				  }
				}
			 stage('Time Lapse') {
			steps {
				sh 'sleep 300'
				  }
				}
			 		stage('clean up') {
			steps {
				sh 'gcloud compute networks subnets delete nasa-vpc-manual-subnet --region=us-central1 --quiet'
				sh 'gcloud compute networks delete  nasa-vpc-auto  nasa-vpc-manual --quiet'
					}
				}
			}
		}
