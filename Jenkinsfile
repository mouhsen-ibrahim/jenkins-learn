pipeline {
    agent { any {  } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
                sh 'echo "hello world" > t1.txt'
                sh 'cat t1.txt'
                sh 'git log'
                retry (3) {
                    sh 'echo hello world'
                }

                timeout(time: 1, unit: 'MINUTES') {
                    sh 'echo "Wait 1 minute"'
                }
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
