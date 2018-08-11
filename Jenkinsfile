pipeline
{
	agent any

	stages
	{
		stage('Compile Code')
		{
			steps 
			{
				bat 'set JAVA_HONE=C:\Program Files\Java\jdk1.8.0_151'
				bat 'set PATH=%PATH%;C:\Program Files\Java\jdk1.8.0_151\bin'
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
