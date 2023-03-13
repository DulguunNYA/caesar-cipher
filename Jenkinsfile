pipeline {
    agent any

    stages {
        stage('Preparing gradlew') {
            steps {
                sh 'chmod +x gradlew'
                echo "prepariiiiiing"
            }
        }
        stage('test') {
            steps {
                sh './gradlew test'
                echo "testiiiiiiing"
            }
        }
        stage('build') {
            steps {
                sh './gradlew build'
                echo "buildiiiiiing"
            }
        }
        //stage('Release') {
        //    steps {
        //
              // Run any necessary setup steps, such as configuring credentials
    	//      sh './gradlew clean build publish'
    	      // Any additional steps, such as tagging the release in Git or sending notifications
        //    }
        //}
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
