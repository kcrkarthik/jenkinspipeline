pipeline
{
	agent any
	
	parameters
	{
		string(name: 'staging_tomcat', defaultValue:'13.232.202.242', description:'Tomcat instance for Staging')
		string(name: 'prod_tomcat', defaultValue:'13.233.12.14', description:'Tomcat instance for Production')
	}
	
	triggers
	{
		pollSCM('* * * * *')
	}
	
	stages
	{
		stage('Compile Code')
		{
			steps 
			{
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

		stage('Deployments')
		{
			parallel
			{
				stage('Deploy to STAGE')
				{
					steps
					{
						bat "C:/cmder/vendor/git-for-windows/usr/bin/scp.exe -i 'C:/Users/kchokkar/Downloads/MyEc2Pair.pem' -o StrictHostKeyChecking=no 'C:/Program Files (x86)/Jenkins/workspace/FullyAutomatedWithAWS/webapp/target/webapp.war' ec2-user@${params.staging_tomcat}:/var/lib/tomcat7/webapps"
					}
				}
				
				stage('Deploy to PROD')
				{
					steps
					{
						bat "C:/cmder/vendor/git-for-windows/usr/bin/scp.exe -i 'C:/Users/kchokkar/Downloads/MyEc2Pair.pem' -o StrictHostKeyChecking=no 'C:/Program Files (x86)/Jenkins/workspace/FullyAutomatedWithAWS/webapp/target/webapp.war' ec2-user@${params.prod_tomcat}:/var/lib/tomcat7/webapps"
					}
				}
				
			}
		}
	}
}
