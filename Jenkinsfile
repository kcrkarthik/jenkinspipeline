pipeline
{
	agent any
	
	parameters
	{
		string(name: 'staging-tomcat', defaultValue:'13.232.202.242', description:'Tomcat instance for Staging')
		string(name: 'prod-tomcat', defaultValue:'13.233.12.14', description:'Tomcat instance for Production')
	}
	
	triggers
	{
		pollSCM('* * * * *')
	}

	stage('Deployments')
	{
		parallel
		{
			stage('Deploy to STAGE')
			{
				sh "cp -i 'C:\Users\kchokkar\Downloads\MyEc2Pair.pem' **/target.war ec2-user@{params.staging-tomcat}:/var/lib/tomcat7/webapps"
			}
			
			stage('Deploy to PROD')
			{
				sh "cp -i 'C:\Users\kchokkar\Downloads\MyEc2Pair.pem' **/target.war ec2-user@{params.prod-tomcat}:/var/lib/tomcat7/webapps"
			}
			
		}
	}
}
