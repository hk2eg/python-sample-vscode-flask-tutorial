pipeline{
    agent{
        label "agent-1"
    }
    environment{
        random_var='Jenkins-Docker-Push-Test'
    }
    stages{
        stage("build Docker image"){
            steps{
                sh "docker build -t hk2802/flask-sample:v${BUILD_NUMBER} ."
            }
        }
        stage("Push Docker image"){
            steps{
                sh "docker push hk2802/flask-sample:v${BUILD_NUMBER}"
            }
        }
    }
}