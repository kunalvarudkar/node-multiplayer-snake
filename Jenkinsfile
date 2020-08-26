// name of node which we have created to connect jenkins server to appserver
node ('ubuntu-appserver'){  
    def app // variable
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
   
    stage('Build-and-Tag') {
    /* This builds the actual image; synonymous to
         * docker build on the command line */
        app = docker.build("kunalvarudkar/snakegame",".")
    }
    stage('Post-to-dockerhub') {
        // this is registry for pushing to dockerhub
        docker.withRegistry('https://registry.hub.docker.com', 'Dockerhub') {
            app.push("latest")
        			} 
         }
    // invoke docker compose
    stage('Pull-image-server') {
        sh "docker-compose down"
        sh "docker-compose up -d"
      }
    
}
