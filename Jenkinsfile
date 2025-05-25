pipeline{
    agent{
        label "java"
    }
    environment{
        XYZ='ITI ITI ITI'
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