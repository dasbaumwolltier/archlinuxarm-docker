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
                sh 'make image-base'
                sh 'docker tag archlinux/archlinuxarm:base dasbaumwolltier/archlinuxarm:aarch64'
                withCredentials([usernamePassword(credentialsId: CREDENTIAL_ID, usernameVariable: 'HUB_USER', passwordVariable: 'HUB_PASS')]) {
                    sh 'echo "$HUB_PASS" | docker login --username "$HUB_USER" --password-stdin'
                    sh 'docker push dasbaumwolltier/archlinuxarm:aarch64'
                }
            }
        }
    }
}