node{
   stage('SCM Checkout'){
      git credentialsId: 'saigit', url: 'https://github.com/saikumard99/webapp.git'
   }
   stage('Mvn Package'){
     sh 'mvn clean package'
   }
   stage('Build Docker Image'){
     sh 'docker build -t kumard99/my-tomcat2 .'
   }
   stage('Build push Image'){
    withCredentials([string(credentialsId: 'dockerpswd', variable: 'dockerpasswd')]) {
     sh "docker login -u kumard99 -p ${dockerpasswd}"
     }
     sh 'docker push kumard99/my-tomcat2'
  }
}