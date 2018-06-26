pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('build') {
            steps {
                sh 'python --version'
                sh 'echo "Test Pipeline"'
                sh """
                echo $WORKSPACE
                cd $WORKSPACE
                tar -zcvf tarfiles.tar.gz tarfiles
                """
            }
        }
    }
}
