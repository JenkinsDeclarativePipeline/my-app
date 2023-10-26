node('maven')
{
    /*properties([
        string(name: 'Branch_Name', defaultValue: 'master', description: 'Enter Branch name')
    ])*/
    stage('SCM_Checkout')
    {
        checkout scmGit(branches: [[name: '*/master']], 
        extensions: [], 
        userRemoteConfigs: [[credentialsId: 'JenkinsDeclarativePipeline', url: 'https://github.com/JenkinsDeclarativePipeline/my-app.git']]
        )
    }
    stage('Maven_Build')
    {
        def mvn = tool name: 'mvn-3.9.5', type: 'maven'
        sh "${mvn}/bin/mvn clean package"
    }
}
