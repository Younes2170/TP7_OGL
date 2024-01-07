pipeline {
    agent any

    stages {
        stage('Test') {
            steps {

            }
        }

        stage('Code Analysis') {
            steps {

            }
        }

        stage('Code Quality') {
            steps {
                // Verify Quality Gates status (replace with your actual task)
                 bat "./gradlew sonarqube"
            }
        }

        stage('Build') {
            steps {

            }
        }

        stage('Deploy') {
            steps {

            }
        }

        stage('Notification') {
            steps {
                script {
                    // Notify on successful deployment
                    echo 'Sending success notification to the development team...'

                    // Add the notifyEvents step here
                    notifyEvents(token: '8e1klwd2f_1nqfpoz7vgml3r8hs7veuq', message: 'Hello <b>world</b>')
                }
            }
        }
    }

    post {
        failure {
            script {

            }
        }
    }
}
