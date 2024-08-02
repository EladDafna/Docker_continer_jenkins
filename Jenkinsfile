pipeline {
    agent any
    environment {
        DOCKERHUB_USER = credentials('DOCKERHUB_USER')
        DOCKERHUB_PASSWORD = credentials('DOCKERHUB_PASSWORD')
    }
    stages {
        stage('Setup') {
            steps {
                script {
                    sh """
                        sudo apt update
                        sudo apt install -y openssh-server openssh-client
                        sudo apt install -y net-tools
                        sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
                        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
                        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu \$(lsb_release -cs) stable"
                        sudo apt-get update
                        sudo apt-get install -y docker-ce
                        docker version
                        sudo groupadd docker || true
                        sudo usermod -aG docker \${USER}
                        docker run hello-world
                    """
                }
            }
        }
    }
}
