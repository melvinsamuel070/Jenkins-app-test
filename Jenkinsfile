pipeline {
    agent any
    stages {
        stage("Test") {
            steps {
                echo "Welcome to Your first Multibranch Jenkins-class"
            }
        }
        stage("checkout something") {
            steps {
                sh '''
                    echo "Welcome" > index.txt
                '''
            }
        }
        stage("rolling") {
            steps {
                sh '''
                    echo $HOME
                    pwd
                    echo "Hello World" taller.txt
                '''
            }
        }
        stage("Install Nginx") {
            steps {
                script {
                    def password = env.MY_SUDO_PASSWORD  // Use an environment variable instead of hardcoding
                    
                    // Update and install Nginx
                    sh "echo ${password} | sudo -S apt-get update"
                    sh "echo ${password} | sudo -S apt upgrade -y"
                    sh "echo ${password} | sudo -S apt-get install nginx -y"
                    sh "echo ${password} | sudo -S systemctl enable nginx"
                    sh "echo ${password} | sudo -S systemctl start nginx"
                }
            }
        }
        stage("Build") {
            steps {
                script {
                    // Change ownership and set up directory
                    sh "sudo chown -R jenkins:jenkins /var"
                    sh "sudo rm -rf /var/www"
                    sh "sudo mkdir /var/www"
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    // Clone repository to web server directory
                    sh "sudo git clone https://github.com/monyslim/pix-mix.git /var/www/html"
                }
            }
        }
    }
    
