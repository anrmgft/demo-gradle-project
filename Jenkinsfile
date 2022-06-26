pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                //git branch: 'main', url: 'https://github.com/anrmgft/hello-springrest.git'

                // Run Maven on a Unix agent.

                /* withGradle {
                sh './gradlew sonarqube'
                } */

                withSonarQubeEnv('sonarqube-community') {
                sh "./gradlew sonarqube"
                }

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Publish') {
            steps{
                sshagent(['github-ssh']) {
                            sh 'git tag BUILD-1.0.${BUILD_NUMBER}'
                            sh 'git push --tags'
                }
            }
        }
    }
}