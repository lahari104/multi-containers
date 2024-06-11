pipeline{
    agent{
        label 'micro-service'
    }
    triggers{
        pollSCM('* * * * *')
    }
    environment{
        DOCKER_HUB_CREDENTIALS = credentials('docker_hub_PAT')
        TAG                    = "${env.BUILD_NUMBER}"
    }
    stages{
        stage('clone'){
            steps{
                git url: "https://github.com/lahari104/multi-containers.git",
                    branch: "main"
            }
        }
        stage('build and deploy'){
            steps{
                sh 'docker compose build'
                sh 'echo ${DOCKER_HUB_CREDENTIALS_PSW} | docker login -u ${DOCKER_HUB_CREDENTIALS_USR} --password-stdin'
                sh 'docker compose push'
                sh 'docker compose up -d'
                sh 'docker container ls -a'
            }
        }
    }
}