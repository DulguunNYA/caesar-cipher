pipeline {
    agent any

    triggers {
        //    |------ Minute (0-59)
        //    | |------ Hour (0-23)
        //    | | |------ Day of the month (1-31)
        //    | | | |------ Month (1-12)
        //    | | | | |------ Day of the Week (1-7, Monday to Sunday)
        //cron('0 */6 * * *') //regular builds
        pollSCM('0 */6 * * *') //polling for changes

    }
     environment {
        CloneRepo = https://github.com/DulguunNYA/caesar-cipher.git
        PublishRepo = "DulguunNYA/caesar-cipher"
        PublishRepoUser = "DulguunNYA"
        PublishRepoName = "caesar-cipher"
    }   

    stages {
        stage('Preparing gradlew') {
            steps {
                sh 'chmod +x gradlew'
                echo "prepariiiiiing"

            }
             post {
                success {
                    echo 'PREPARING GRADLEW OK'
                }
                failure { 
                    echo 'PREPARING GRADLEW Failure'
                }
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
        stage('Run & Test program') {
            steps {
                script {
                    def output =  sh(returnStdout: true, script: 'java -jar ./build/libs/caesar-cipher.jar').trim()
                    if (output.contains('Message:')) {
                        echo "  'Message:' ok"
                    } else {
                        echo "  'Message:' Error"
                        exit 1
                    }
                }
            }
            post {
                success {
                    echo 'Run & Test program OK'
                }
                failure { 
                    echo 'Run & Test program Failure'
                }
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
