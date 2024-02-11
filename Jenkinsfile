pipeline {
    agent { label 'jdk-8' }
    options { 
        timeout(time: 30, unit: 'MINUTES') 
    }
    triggers { 
        pollSCM('* * * * *') 
    }
    tools {
        jdk 'jdk-8' 
    }
    stages {
        stage ('git') {
            steps {
                git url: 'https://github.com/nkishore555/game-of-life.git',
                    branch: 'master'
            }

        }
        stage ('build and package') {
            steps {
                sh script: 'mvn package'
            }

        }
        stage ('report') {
            steps {
                archiveArtifacts artifacts: '**/gameoflife.war'
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }

        }
    }
    
}
