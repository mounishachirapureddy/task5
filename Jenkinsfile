pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your CodeCommit repository
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']], // Change to your desired branch
                    userRemoteConfigs: [[
                        credentialsId: '352d12d8-610e-4a17-bf7d-d9fca31128bc',
                        url: 'https://git-codecommit.ap-south-1.amazonaws.com/v1/repos/Snapcoins'
                    ]]
                ])
            }
        }

     /*   stage('Run Jenkinsfile') {
            steps {
                // Run the Jenkinsfile from your repository
                sh 'jenkinsfile.sh' // Replace with your Jenkinsfile execution command
            }
        } */
    }
}
