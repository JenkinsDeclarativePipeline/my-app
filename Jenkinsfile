node('maven')
{
    properties([
        string(name: 'Branch_Name', defaultValue: 'master', description: 'Enter Branch name')
    ])
    stage('SCM_Checkout')
    {
        checkout scmGit(branches: [[name: '*/master']], 
        extensions: [], 
        userRemoteConfigs: [[credentialsId: 'JenkinsDeclarativePipeline', url: 'https://github.com/JenkinsDeclarativePipeline/my-app.git']]
        )
    }
}
