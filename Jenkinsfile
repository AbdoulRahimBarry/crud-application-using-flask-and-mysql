/* import shared library */
@Library('jenkins-shared-library')_

pipeline {
    agent none
    stages {
        stage('Check css syntax') {
            agent { docker { image 'eeacms/csslint' } }
            steps {
                sh 'csslint  \${WORKSPACE}/source_code/static/css/_all-skins.min.css'
            }
        }
        stage('Check bash syntax') {
            agent { docker { image 'koalaman/shellcheck-alpine:stable' } }
            steps {
                script { bashCheck }
            }
        }
    }
    post {
    always {
       script {
         /* Use slackNotifier.groovy from shared library and provide current build result as parameter */
         clean
         slackNotifier currentBuild.result
    }
   }
  }
}
