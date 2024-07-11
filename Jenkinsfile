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
        stage("install nginx"){
            steps {
                sh '''
                 // Define the password (replace with a secure method in production)
                    def password = "<your_password>"
                    
                    // Execute commands using sudo with -S option
                    sh "echo '${password}' | sudo -S apt-get update"
                    sh "echo '${password}' | sudo -S apt upgrade -y"
                    sh "echo '${password}' | sudo -S apt-get install nginx -y"
                    sh "echo '${password}' | sudo -S systemctl enable nginx"
                    sh "echo '${password}' | sudo -S systemctl start nginx"
                '''
            }
        }
        stage("build"){
            steps{
                sh '''
                    sudo chown -R jenkins:jenkins /var*
                    cd /var
                    sudo rm -rf www
                    sudo mkdir www
                    cd /var/www

                '''
            }
        }
        stage("deploy"){
            steps{
                sh '''
                    cd /var/www
                    sudo git clone https://github.com/monyslim/pix-mix.git html
                '''
            }
        }
    }
}
