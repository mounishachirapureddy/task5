pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-1'
        AWS_ACCESS_KEY_ID     = credentials('AKIARGWR6CGSTJVCA2QY')
        AWS_SECRET_ACCESS_KEY = credentials('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')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    def repositoryName = 'Snapcoins'
                    def branchName = 'main' // or your desired branch name

                    checkout([$class: 'GitSCM', 
                              branches: [[name: "refs/heads/${branchName}"]],
                              doGenerateSubmoduleConfigurations: false,
                              extensions: [[$class: 'CleanCheckout']],
                              submoduleCfg: [],
                              userRemoteConfigs: [[url: "https://git-codecommit.${AWS_DEFAULT_REGION}.amazonaws.com/v1/repos/${repositoryName}"]]])
                }
            }
        }

        stage('Build') {
            steps {
               
                
                dir('client') {
                    bat 'npm install'
                    //bat 'npm test'
                }

                dir('servers/gamer-module') {
                    bat 'npm install'
                    //bat 'npm test'
                }

                dir('servers/merchant-module') {
                    bat 'npm install'
                    //bat 'npm test'
                }

                dir('servers/gaming-vendor-module') {
                    bat 'npm install'
                    //bat 'npm test'
                }

                dir('servers/general-module') {
                    bat 'npm install'
                    //bat 'npm test'
                    
                }
            }
        }

    }  
}
