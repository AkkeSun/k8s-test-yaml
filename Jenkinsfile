pipeline {
    agent any

    stages {
        stage('[Master] k8s deploy') {
            when {
                branch 'master'
            }
            steps {
                sh 'kubectl apply -f ./od-test/prod/namespace.yaml'
                sh 'kubectl apply -f ./od-test/prod/pv.yaml'
                sh 'kubectl apply -f ./od-test/prod/pvc.yaml'
                sh 'kubectl apply -f ./od-test/prod/configmap.yaml'
                sh 'kubectl apply -f ./od-test/prod/service.yaml'
                sh 'kubectl apply -f ./od-test/prod/hpa.yaml'
                sh 'kubectl apply -f ./od-test/prod/deployment.yaml'
            }
        }
    }

    /*
    // ------ use Slack Notification plugin
    post {
        success {
            slackSend color: "good", message: "✅Build Success!\\n\\n\\n PROJECT             : ${JOB_NAME}\\n BRANCH             : ${env.BRANCH_NAME}\\n JENKINS URL     : <${env.RUN_DISPLAY_URL}|Blue Ocean Link>\\n LAST_COMMIT  : ${LAST_COMMIT}"
        }
        failure {
            slackSend color: "danger", message: "❌Build Fail!\\n\\n\\n PROJECT             : ${JOB_NAME}\\n BRANCH             : ${env.BRANCH_NAME}\\n JENKINS URL     : <${env.RUN_DISPLAY_URL}|Blue Ocean Link>\\n LAST_COMMIT  : ${LAST_COMMIT}"
        }
    }
    */
}
