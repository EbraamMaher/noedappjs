pipeline{

    agent {label 'agent1'}
    
    stages{
        stage('Build image'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'username',passwordVariable: 'password')]){
                sh "docker build . -t node-app:5"
                sh "docker login -u $username -p $password"
                sh "docker run -d -p 65:3000 node-app:5"
                
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
