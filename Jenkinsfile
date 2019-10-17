
node {

   stage('Clone Repository') {
        // Get some code from a GitHub repository
        git 'https://github.com/anverma007/spring-petclinic.git'
    
   }
   stage('Build Maven Image') {
        docker.build("maven-build")
   }
   
   stage('Run Maven Container') {
        
        //Run maven image
        sh "docker run --rm --name maven-build-container maven-build"
   }
   
   stage('Deploy Spring Boot Application') {
       
        sh "docker run --name java-deploy-container --volumes-from maven-build -d -p 8080:8080 denisdbell/petclinic-deploy"
   }

}
