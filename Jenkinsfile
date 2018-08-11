pipeline
{
	agent any

	stages
	{
		stage('Compile Code')
		{
			steps 
			{
				env.JAVA_HOME="${tool 'jdk-8u151'}"
				env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
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
