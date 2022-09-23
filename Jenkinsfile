node{
    stage('Checkout'){
        git 'https://github.com/mrvincentoti/hello-world-maven.git'
    }
    stage('Compile Package'){
        // Get maven home path
        def mvnHome = tool name: '/opt/apache-maven-3.8.6', type: 'maven'
        sh "${mvnHome}/bin/mvn clean package"
    }
    // Email notification
    stage('Email Notification'){
        mail bcc: '', body: '''Hi,
        Welcome to Jenkins pipeline Alerts.
        Thank you,
        Vincent''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'mrvincentoti@gmail.com'
    }
}