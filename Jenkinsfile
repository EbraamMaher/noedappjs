pipeline{

    agent {label 'agent1'}
    
    stages{
        stage('Build image'){
            steps{
                withCredentials(usernameColonPassword(credentialsId: 'docker', userVariable: 'username',passwordVariable: 'password')) {
                sh "docker build . -t node-app:$BUILD_TAG"
                sh "docker login -u $username -p $password"
                sh "docker run -d -p 90:3000 node-app:$BUILD_TAG"
                sh "docker push 852456000/nodejs:$BUILD_TAG"
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
