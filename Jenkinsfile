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
   mvn clean verify sonar:sonar -Dsonar.projectKey=myproject -Dsonar.host.url=http://23.20.195.244:9002 -Dsonar.login=sqp_50f3512e10a6e279f7b2e8265c59673eb6ed5fc0
   
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
