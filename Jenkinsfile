pipeline {
    agent any
    stages {
        stage('Run Script') {
            steps {
                sh './run.sh'
            }
        }
        stage('Archive Output') {
            steps {
                archiveArtifacts artifacts: 'output.txt', onlyIfSuccessful: true
            }
        }
    }
    post {
        success {
            mail to: 'jacksonrenald495@gmail.com',
                 subject: "Jenkins Job SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Job passed! View output: ${env.BUILD_URL}"
        }
        failure {
            mail to: 'jacksonrenald495@gmail.com',
                 subject: "Jenkins Job FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Job failed! View console output: ${env.BUILD_URL}"
        }
    }
}
