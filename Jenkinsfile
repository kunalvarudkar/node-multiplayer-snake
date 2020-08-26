node ('ubuntu-appserver')
{
    stage('Git Clone')
    {
        checkout scm
    }

    stage('Container Build')
    {
        docker.withRegistry('https://registry.example.com', 'dockerhub')
        {
            def customImage = docker.build("kunalvarudkar:${env.BUILD_ID}")
        }
    }

    stage('Push-Dockerhub')
    {
        docker.withRegistry('https://registry.hub.docker.com','dockerhub')
        {
            customImage.push("latest")
        }
    }

    stage('Pull docker image')
    {
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}




