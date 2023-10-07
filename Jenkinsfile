pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-1'
        AWS_ACCESS_KEY_ID     = credentials('AKIARGWR6CGS3SJQEKM4')
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
