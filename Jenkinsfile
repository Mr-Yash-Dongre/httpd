pipeline{
    agent any
    stages{
        stage('git clone'){
            steps{
                dir('/docker-httpd/22q2'){
                    sh "git clone -b 22q2 https://github.com/Mr-Yash-Dongre/httpd.git"
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
                sh "docker run --name httpd-2.0 -itdp 91:80 httpd"
                sh "chmod -R 777 /docker-httpd/22q2/httpd/index.html"
                sh "docker cp /docker-httpd/22q2/httpd/index.html httpd-2.0:/usr/local/apache2/htdocs"
            }
        }
    }
}
