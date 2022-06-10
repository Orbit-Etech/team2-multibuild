pipeline{
  agent any
  stages{
  	stage('version-control'){
  		steps{
  			checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkins-build', url: 'https://github.com/Orbit-Etech/team2-multibuild.git']]])
  		}
  	}
    stage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            sh 'uptime'
          }
        }
        stage('sub-job2'){
          steps{
             sh 'lscpu'
          }
        }
        stage('sub-job3'){
          steps{
            sh 'lsblk'
          }
        }
      }
    }
    stage('deployment'){
      when {
          branch 'develop'
      }
      steps{
    		sh 'cat /etc/passwd'
    	}
    }
  }
}
