pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                // Step 1: Lancement des tests unitaires.
                sh 'gradle test'

                // Step 2: Archivage des résultats des tests unitaires.
                junit 'build/test-results/test/*.xml'

                // Step 3: Génération des rapports de tests Cucumber.
                // Assuming you have a Cucumber task in your Gradle build script
                sh 'gradle cucumber'
            }
        }

        stage('Code Analysis') {
            steps {
                // Step: Analyser la qualité du code avec SonarQube.
                sh 'gradle sonarqube'
            }
        }

        stage('Code Quality') {
            steps {
                // Step: Vérifier l'état de Quality Gates.
                // Assuming you have a task to check Quality Gates status in your Gradle build script
                sh 'gradle checkQualityGates'
            }
        }

        stage('Build') {
            steps {
                // Step 1: Génération du fichier Jar.
                sh 'gradle build'

                // Step 2: Génération de la documentation.
                sh 'gradle javadoc'

                // Step 3: Archivage du fichier Jar et de la documentation.
                archiveArtifacts artifacts: 'build/libs/*.jar, build/docs/javadoc/**/*', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                // Step: Déployer le fichier Jar généré dans https://mymavenrepo.com/.
                // Replace this with your actual deployment command
                // For simplicity, let's assume copying the file to a destination
                sh 'cp build/libs/*.jar /path/to/deployment/'
            }
        }

        stage('Notification') {
            steps {
                script {
                    // Notification for successful deployment
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
                // Notification for pipeline failure
                echo 'Sending failure notification to the development team...'

                // Replace the following commands with your actual notification commands
                // Assuming you have plugins or scripts to send notifications
                // You may use email, Slack, Google Chrome, and Signal plugins
                sh 'send_email_notification'
                sh 'send_slack_notification'
                sh 'send_chrome_notification'
                sh 'send_signal_notification'
            }
        }
    }
}
