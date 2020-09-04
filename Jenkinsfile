node ('Ubuntu-app-agent')
{
    def customImage
    stage('Git Clone')
    {
       checkout scm
    }
    
    stage('Checking code - SAST')
    {
        build 'SECURITY-SAST-SNYK'
    }

    stage('Container Build')
    {
        
        customImage = docker.build("kunalvarudkar/snake")
        //sh 'echo Container Builing phase'
    }

    stage('Push-Dockerhub')
    {
       // sh 'echo Docker push phase'
        docker.withRegistry('https://registry.hub.docker.com','dockerhub')
        {
            customImage.push("latest")
        }
    }
    
    stage('Container Scanner')
    {
        build 'Security-Container_Scanner-Aqua MicroScanner'
    }

    stage('Pull docker image')
    {
       // sh 'echo Docker pull phase'
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
    
    stage('Checking Vuln - DAST')
    {
        build 'Security-DAST-OWASP_ZAP'
    }
}




