pipeline
{
	agent any

	stages
	{
		stage('Compile Code')
		{
			steps 
			{
				bat 'set JAVA_HONE=C:\\Program Files\\Java\\jdk1.8.0_151'
				bat 'set PATH=%PATH%;C:\\Program Files\\Java\\jdk1.8.0_151\\bin'
				bat 'mvn clean package'
			}
			post 
			{
                		success 
				{
                    			echo 'Maven Build Success. Moving WAR to Archive...'
                    			archiveArtifacts artifacts: '**/target/*.war'
				}
			}
		}

		stage('Deploy to Staging')
		{
			steps 
			{
				echo "BUILD"
				build job: 'Deploy to Staging Tomcat'
			}
		}
		
		stage('Deploy to Prod')
		{
			steps 
			{
				echo "DEPLOY"
				
				timeout(time:5, unit:days")
				{
					input message:'IS PROD DEPLOYMENT APPROVED???'
				}
				
				build job: 'Deploy to Production ' 
			}
			post
			{
				success
				{
					echo 'Code deployed to prod'
				}
				failure
				{
					echo 'Code deployed to prod FAILED'
				}
			}
		}
	}
}
