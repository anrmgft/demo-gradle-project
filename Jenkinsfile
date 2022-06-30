pipeline {
    agent any
    stages {
    /* stage('Registry') {
                steps{
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'TOKEN', usernameVariable: 'USERNAME')]) {
                       sh "./gradlew publish"
                    }
                    }
                } */
    stage('NEXUS') {
                    steps{
                        withCredentials([usernamePassword(credentialsId: 'SonatypeNexus', passwordVariable: 'NEXUSPASSWORD', usernameVariable: 'NEXUSUSERNAME')]) {
                           sh "./gradlew publish"
                        }
                        }
                    }
        /* stage('Build') {
            steps {

                 *//* withSonarQubeEnv('sonarqube-community') {
                sh "./gradlew sonarqube"
                } *//*

                withGradle {
                    sh "./gradlew publish"
                    }
            }
        } */


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