pipeline{
    agent any
    stages{
        stage('git clone'){
            steps{
                dir('/docker-httpd/22q3'){
                    sh "git clone https://github.com/Mr-Yash-Dongre/httpd.git"
                }
            }
        }
        stage('httpd image download'){
            steps{
                sh "systemctl start docker"
                sh "docker pull httpd"
            }
        }
        stage('create container'){
            steps{
                sh "docker run --name httpd-3.0 -itdp 8080:80 httpd"
                sh "chmod -R 777 /docker-httpd/22q3/index.html"
                sh "docker cp /docker-httpd/22q3/index.html httpd-3.0:/usr/local/apache2/htdocs"
            }
        }
    }
}
