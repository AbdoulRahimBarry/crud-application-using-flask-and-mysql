/* import shared library */
@Library('jenkins-shared-library')_

pipeline {
    agent none
    stages {
        stage('Check css syntax') {
            agent { docker { image 'eeacms/csslint' } }
            steps {
                sh 'csslint  \${WORKSPACE}/source_code/static/css/_all-skins.min.css'
                sh 'csslint  \${WORKSPACE}/source_code/static/css/dataTables.bootstrap.css'
            }
        }
		/*stage('Check python syntax') {
		    agent { docker { image 'eeacms/pylint' } }
			steps {
			    sh 'pylint  \${WORKSPACE}/source_code/module/database.py'
			}
		}*/
		stage('Check Dockerfile and Dockerfile-mysql yntax') {
		    agent { docker { image 'hadolint/hadolint' } }
			steps {
			    sh 'hadolint \${WORKSPACE}/Dockerfile-app'
                            sh 'hadolint \${WORKSPACE}/Dockerfile-mysql'
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
