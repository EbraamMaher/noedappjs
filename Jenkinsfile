pipeline{

    agent {label 'agent1'}
    
    stages{
        stage('Build image'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'username',passwordVariable: 'password')]){
                sh "docker build . -t node-app:5"
                sh "docker login -u $username -p $password"
                sh "docker image ls"
                sh "docker run -d -p 74:3000 node-app:5"
                sh "docker push node-app"
            }
            
            }
            post {
                success {
                    sh "docker image ls"
                }
                
                }

        }

    }
}
