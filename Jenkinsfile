pipeline {
    agent { label 'jdk_11' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/dimplevayigandla1005/game-of-life.git',
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
