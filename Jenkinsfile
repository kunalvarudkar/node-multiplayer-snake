node ('Ubuntu-app-agent')
{
    stage('Git Clone')
    {
       checkout scm
    }

    stage('Container Build')
    {
        
       // def customImage = docker.build("kunalvarudkar:${env.BUILD_ID}")
        sh 'echo Container Builing phase"
    }

    stage('Push-Dockerhub')
    {
        sh 'echo Docker push phase"
       // docker.withRegistry('https://registry.hub.docker.com','dockerhub')
       // {
         //   customImage.push("latest")
       // }
    }

    stage('Pull docker image')
    {
        sh 'echo Docker pull phase
       // sh "docker-compose down"
       // sh "docker-compose up -d"
    }
}




