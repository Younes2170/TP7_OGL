pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                // Step 1: Run unit tests
                bat 'gradle test'

                // Step 2: Archive test results
                junit 'build/test-results/test/*.xml'

                // Step 3: Generate Cucumber reports (assuming you have a Cucumber task)
                bat 'gradle cucumber'
            }
        }

        stage('Code Analysis') {
            steps {
                // Analyze code quality with SonarQube
                bat 'gradle sonarqube'
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
                // Notify on pipeline failure
                echo 'Sending failure notification to the development team...'

                // Replace the following commands with your actual notification commands
                // Assuming you have plugins or scripts to send notifications
                // You may use email, Slack, Google Chrome, and Signal plugins
                bat 'send_email_notification'
                bat 'send_slack_notification'
                bat 'send_chrome_notification'
                bat 'send_signal_notification'
            }
        }
    }
}
