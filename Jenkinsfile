pipeline {
  agent any
  stages {
	stage('CleanWorkspace') {
            steps {
                cleanWs()
            }
    }	
		
	stage('Git merge') {
      steps {
        bat '''
		git init	
		git remote add origin https://git.chetu.com/DevOps_Automation/ASP.NET_Core5_WebApp.git
		git pull origin update_home_page
		
        git fetch --all
		git branch 
		git checkout devlop
		git config --global credential.helper wincred
		git merge update_home_page
		git push -f origin devlop
			

		'''
      }
	
	post {
    success {
        mail to: "subhashsingh95@gmail.com",
                subject: "SUCCESS: $JOB_NAME",
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
    }

    failure {
        mail to: "subhashsingh95@gmail.com",
                subject: "FAILURE: $JOB_NAME",
                body: "Job Result: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info : ${env.BUILD_URL}"
    }
  }
  }
  }
	}