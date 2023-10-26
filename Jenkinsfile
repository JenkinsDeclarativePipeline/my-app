node('maven')
{
    git_branch = properties([
        string(name: 'Branch_Name', defaultValue: 'master', description: 'Enter Branch name')
    ])
    stage('SCM_Checkout')
    {
        checkout scmGit(branches: [[name: '*/${git_branch.Branch_Name}']], 
        extensions: [], 
        userRemoteConfigs: [[credentialsId: 'JenkinsDeclarativePipeline', url: 'https://github.com/JenkinsDeclarativePipeline/my-app.git']]
        )
    }
}