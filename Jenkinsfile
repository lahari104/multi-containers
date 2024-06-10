pipeline{
    agent{
        label 'micro-service'
    }
    triggers{
        pollSCM('* * * * *')
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
                sh 'echo $DOCKER_PASSWORD | docker login --username $DOCKER_USERNAME --password-stdin'
                sh 'docker compose push'
                sh 'docker compose up -d'
                sh 'docker container ls -a'
            }
        }
    }
}