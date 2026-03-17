pipeline {
    agent any
    stages{
        stage('git cloned'){
            steps{
                git url:'https://github.com/Janani2-1/php-project', branch: "master"
              
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t jan216/5sepimage:v1 .'
                    sh 'docker images'
                }
            }
        }
          stage('Docker login') {
            steps {
                script {
                    sh 'echo "21*JanRT06" | docker login -u jan216 --password-stdin'
                    sh 'docker push jan216/5sepimage:v1'
                }
            }
        }
        
     stage('Deploy') {
            steps {
               script {
                   def dockerrm = 'sudo docker rm -f My-first-containe2211 || true'
                    def dockerCmd = 'sudo docker run -itd --name My-first-containe2211 -p 8083:80 jan216/5sepimage:v1'
                    sshagent(['sshkeypair']) {
                        //chnage the private ip in below code
                        // sh "docker run -itd --name My-first-containe2111 -p 8083:80 akshu20791/2febimg:v1"
                         sh "ssh -o StrictHostKeyChecking=no ubuntu@3.110.110.134 ${dockerrm}"
                         sh "ssh -o StrictHostKeyChecking=no ubuntu@3.110.110.134 ${dockerCmd}"
                    }
                }
            }
        }
    }
}
