pipeline{

agent any
stages{
/* stage('initialize'){
    steps{
checkout scm
}
} */

stage('compile'){
    steps{
 sh '''
mvn compile
'''
}
}


/*stage('unittest'){
  steps{  
sh '''
mvn test
'''
}  
  

post{
        always{
             junit testResults:"target/surefire-reports/*.xml"
        }
    }
}*/
stage('build'){
    steps{
sh '''
mvn package -DskipTests
'''
}
}
stage('SonarScan'){

   sh '''
   mvn clean verify sonar:sonar -Dsonar.projectKey=myproject -Dsonar.host.url=http://54.221.178.233:5678 -Dsonar.login=sqp_1b996ebadcd4ad166f710e565364cc7cf5b7e5fb
   
   '''

}

stage('archive'){
steps{
archiveArtifacts artifacts: '**/*.war'
}
}

/*stage('Deploy'){
steps{
sh '''

    
    docker build -t mywebapp .
    docker run -d -p 5555:8080 mywebapp
'''
}
}*/
}
}
