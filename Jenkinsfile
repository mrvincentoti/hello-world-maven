node{
    stage('Checkout'){
        git 'https://github.com/mrvincentoti/hello-world-maven.git'
    }
    stage('Compile Package'){
        // Get maven home path
        def mvnHome = tool name: '/opt/apache-maven-3.8.6', type: 'maven'
        sh "${mvnHome}/bin/mvn clean package"
    }
    stage('Deploy to Server(Ubuntu)'){
        sshagent(['ubuntu']) {
             sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@54.91.176.151:/opt/tomcat8/webapps/'
        }
    }
    // Email notification
    stage('Email Notification'){
        mail bcc: '', body: '''Hi,
        Welcome to Jenkins pipeline Alerts.
        Thank you,
        Vincent''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'mrvincentoti@gmail.com'
    }
    stage('Slack Notification'){
        slackSend baseUrl: 'https://hooks.slack.com/services/', 
        channel: '#layer3-notice', 
        color: 'good', 
        message: 'Welcome to Jenkins Slack!', 
        tokenCredentialId: 'slack-jenkins'
    }
}