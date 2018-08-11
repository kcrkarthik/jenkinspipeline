pipeline
{
	agent any

	stages
	{
		stage('Compile Code')
		{
			steps 
			{
				echo %PATH%
				java -version
				echo %HAVA_HOME%
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
			}
		}
		
		stage('Deploy to Prod')
		{
			steps 
			{
				echo "DEPLOY"
			}
		}
	}
}
