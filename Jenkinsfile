pipeline {
    agent any
    stages {
        stage("build & SonarQube analysis") {
            steps {
                withSonarQubeEnv("sonar"){
                     bat './gradlew test'

                }
                bat './gradlew sonar'

            }
        }

        stage("build2 & SonarQube analysis") {
                    steps {




                                timeout(time: 1, unit: 'HOURS') {
                                    waitForQualityGate abortPipeline: true
                                }


                    }
                }
    }
}