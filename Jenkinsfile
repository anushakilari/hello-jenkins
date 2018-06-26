pipeline {
    agent any
    stages {
        stage ('Clean workspace') {
            deleteDir()
        }
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('build') {
            steps {
                sh """
                echo $WORKSPACE
                cd $WORKSPACE
                tar -zcvf tarfiles.tar.gz tarfiles
                """
            }
        }
        stage('deploy') {
            steps {
                sh """
                echo "uploading tar files to jfrog artifactory"
                echo $api_key
                curl -H "X-JFrog-Art-Api:$api_key" -T $workspace/tarfiles.tar.gz "http://13.232.110.160:8081/artifactory/generic-local/tarfiles.tar.gz"
                """
            }
        }
    }
}
