#!groovy

pipeline {
    agent {
         label 'master'
         }
    environment {
        GRADLE_OPTS='-Dorg.gradle.daemon=false'
    }
    options {
         timestamps()
    }
	  stages {
        stage("pulling a project from GitHub") {
            steps {
                git poll: true, url: 'https://github.com/kern-y/final_task_intermine'
				   }
        }
        stage("building an artifact") {
            steps {
			        withGradle {
              sh './gradlew war'
              }
            }
        }
	    	stage("testing an app") {
            steps {
			        withGradle {
              sh './gradlew check'
              }
            }
        }

    }
}
