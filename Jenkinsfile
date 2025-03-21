post {
    always{
        script {
            def jobName = env.JOB_NAME
            def buildNumber = env.BUILD_NUMBER
            def pipelineStatus = currentBuild.result ?: 'UNKNOWN'
            def bannerColor = pipelineStatus.toUpperCase() == 'SUCCESS' ? 'green' : 'red'

            def body = """
                <html>
                <body>
                <div style="border: 4px solid ${bannerColor}; padding: 10px;">
                <h2>${jobName} - Build ${buildNumber}</h2>
                <div style="background-color: ${bannerColor}; padding: 10px;">
                <h3 style="color: white;">Pipeline Status: ${pipelineStatus.toUpperCase()}</h3>
                </div>
                <p>Check the <a href="${BUILD_URL}">console output</a>.</p>
                </div>
                </body>
                </html>
            """

            emailext (
                subject: "${jobName} - Build ${buildNumber} - ${pipelineStatus.toUpperCase()}",
                body: body,
                to: 'ravindrareddy.mukka9@gmail.com',
                from: 'devopstraining17042000@gmail.com',
                replyTo: 'devopstraining17042000@gmail.com',
                mimeType: 'text/html',
            )
        }
    }
}


// Setting up a tigger for the pipeline using Generic Webhook Tigger:
// =================================================================
// 1. Install Generic Webhook Tigger Plugin in Jenkins:
// 	- Go to Jenkins dashboard
// 	- Navigate to manage Jenkins -> Manage Plugins
// 	- In the Available section, search for "Generic Webhook Tigger"
// 	- Install the Plugin and restart the Jenkins if necessary
	
// 2. Configure the Plugin in Jenkins job:
// 	- Create or open the Jenkins job you want to tigger
// 	- In the job configuration, scroll down to Build tigger section
// 	- check the checkbox for "Generic Webhook Tigger"
	
// 3. Configure Post parameters:
// 	- In the post parameters section, add the following
// 		- variable: ref
// 		- Expression(Json): $.ref

// 4. Write a string as Token
// 	- Write any keyword as token that will be used in the webhook URL  (Example Token Name: Jenkins)
	
// 5. Configure Optional filter:
// 	-In the optional filter section, Configure the following:
// 		- Expression: refs/head/branch_name (Replace the branch name with the name of your branch)
// 		- Text: $ref
		
// 6. Configure GitHub Webhook
// 	- Go to your GitHub repository settings
// 	- Navigate to Webhooks
// 	- Click Add Webhook
// 	- In the payload URL field, enter the following URL:
// 		- http://JENKINS_URL/generic-webhook-tigger/invoke?token=TOKEN_HERE
		
// 		- Payload_URL: http://13.233.104.165:8080/generic-webhook-tigger/invoke?token=Jenkins
// 		- Content_type: application/json
// 		- Click on Add Webhook
