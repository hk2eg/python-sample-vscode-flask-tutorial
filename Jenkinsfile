node('agent-1') {
    stage('Build docker image') {
        try {
            sh "docker build -t hk2802/flask-sample:v${BUILD_NUMBER} ."
        }
        catch (exc) {
            echo 'Stage: "Build docker image" has failed! Check Dockerfile for errors.'
            throw exc
        }
    }

    stage('Push docker image') {
        try {
            sh "docker push hk2802/flask-sample:v${BUILD_NUMBER}"
        }
        catch (exc) {
            echo 'Stage: "Push docker image" has failed! Check Dockerhub credentials in Jenkins UI and try again.'
            throw exc
        }
    }
}