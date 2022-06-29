pipeline {
    agent any
    stages {
        stage('Build') {
            steps {

                /* withSonarQubeEnv('sonarqube-community') {
                sh "./gradlew sonarqube"
                } */


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