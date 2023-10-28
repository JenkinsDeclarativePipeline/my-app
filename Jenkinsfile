node('maven')
{
    properties([
        parameters([string(defaultValue: 'master', description: 'Enter branch name', name: 'branch')])
        ])
    def mvn = tool name: 'mvn-3.9.5', type: 'maven'
    stage('SCM_Checkout')
    {
        checkout scmGit(branches: [[name: "*/${params.branch}"]], 
        extensions: [], 
        userRemoteConfigs: [[credentialsId: 'JenkinsDeclarativePipeline', url: 'https://github.com/JenkinsDeclarativePipeline/my-app.git']]
        )
    }
    stage('Maven_Build')
    {
        
        sh "${mvn}/bin/mvn clean package"
    }
    stage('SonarQube_Code_Check')
    {
        sh "${mvn}/bin/mvn sonar:sonar \
            -Dsonar.projectKey=maven-practice \
            -Dsonar.host.url=http://3.27.9.220:9000 \
            -Dsonar.login=sqp_a39cde1e37b3368b3ce32873897575263deaed4a"
    }
    stage('Slack_Notification')
    {
        slackSend baseUrl: 'https://app.slack.com/client/', channel: '#my-app', color: 'good', message: 'Welcome to Jenkins', teamDomain: 'devops', tokenCredentialId: 'slack-cred', username: 'suriyapraba981'
    }
}
