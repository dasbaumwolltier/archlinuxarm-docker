pipeline {
    agent { label 'arm' }

    stages { 
        stage('Build base.tar.xz') {
            steps {
                sh 'docker build -t archlinuxarm-docker-build-image -f build-image/Dockerfile .'
                sh 'docker run -v "$(pwd)/build:/build/build" -v "$(pwd)/output:/build/output" archlinuxarm-docker-build-image'
            }
        }

        stage('Build') {
            steps {
                withCredentials([usernamePassword(credentialsId: CREDENTIAL_ID, usernameVariable: 'HUB_USER', passwordVariable: 'HUB_PASS')]) {
                    sh ''
                }
            }
        }
    }
}