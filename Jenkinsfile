pipeline
{
	agent any

	stages
	{
		stage('Compile Code')
		{
			steps 
			{
				sh 'mvn clean package'
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
