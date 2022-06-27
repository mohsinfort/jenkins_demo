pipeline {
    agent none
    stages {
        stage('non-parallel-stage') {
			agent {
				label 'master'
			}
            steps {
                echo "this stage will executed first"
            }
        }
		stage('Run-tests'){
			parallel {
				stage('build') {
					agent {
						label 'Window_Node'
					}
					steps {
						echo "running tests on slave node"
					}
				}
				
				stage('unit-test') {
					agent {
						label 'master'
					}	
					steps {
						echo "running unit test on master node"
					}
				}
				
				stage('quality') {
					agent {
						label 'Window_Node'
					}
					steps {
						echo "running quality tests on slave node"
					}
				}
				
				stage('deploy') {
					agent {
						label 'master'
					}
					steps {
						echo "running tests on master node"
					}
				}
			}
		}
		
    }
}
