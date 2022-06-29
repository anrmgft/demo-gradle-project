pipeline {
    agent any
    stages {
    stage('Registry') {
                steps{
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'pass', usernameVariable: 'user')]) {
                       sh "echo '${pass}' | docker login ghcr.io -u anrmgft --password-stdin"
                    }
                    }
                }
        stage('Build') {
            steps {

                /* withSonarQubeEnv('sonarqube-community') {
                sh "./gradlew sonarqube"
                } */

                withGradle {
                    sh "./gradlew publish"
                    }
            }
        }


       /* stage('Publish') {
            steps{
                sshagent(['github-ssh']) {
                            sh 'git tag BUILD-1.0.${BUILD_NUMBER}'
                            sh 'git push --tags'
                }
            }
        } */
    }
}