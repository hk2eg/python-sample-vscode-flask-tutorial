node('agent-1') {
    def image = "hk2802/flask-sample"
    def version = env.BUILD_NUMBER

    withCredentials([usernamePassword(
        credentialsId: 'docker-hub-login',
        usernameVariable: 'DOCKER_USR',
        passwordVariable: 'DOCKER_PSW'
    )]) {

        stage('Build docker image') {
            try {
                script {
                    dockerLogin(env.DOCKER_USR, env.DOCKER_PSW)
                    dockerBuild(image, version)
                }
            } catch (exc) {
                echo 'Stage: "Build docker image" has failed! Check Dockerfile for errors.'
                throw exc
            }
        }

        stage('Push docker image') {
            try {
                script {
                    dockerLogin(env.DOCKER_USR, env.DOCKER_PSW)
                    dockerPush(image, version)
                }

            } catch (exc) {
                echo 'Stage: "Push docker image" has failed! Check Image name and verify Dockerhub credentials in Jenkins UI and try again.'
                throw exc
            }
        }
    }
}
