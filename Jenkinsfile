pipeline {
    agent { label "jdk_11" }
    stages {
        stage ( 'vcs' ) {
            steps {
                git url: 'https://github.com/dimplevayigandla1005/game-of-life.git',
                    branch: 'master'
            }
        }
        stage ( 'package' ) {
            steps {
                sh 'mvn package'
            }
        }
        stage('post built') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                onlyIfSucessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }

}