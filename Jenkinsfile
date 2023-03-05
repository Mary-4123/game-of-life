pipeline {
    agent { label 'mary-17' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/Mary-4123/game-of-life.git',
                    branch: 'master'
            }
        }
        stage('package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}

