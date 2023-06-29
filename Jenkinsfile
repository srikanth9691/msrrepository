pipeline
{
    agent any
    stages
    {
      stage('ContinuousDownload')
       {
           steps
           {
              git 'https://github.com/srikanth9691/msrrepository.git'
           }
       }
    
   stage('ContinuousBuilt')
       {
           steps
          {
            sh 'mvn package'
          } 
       }
    
   stage('ContinuousDeployment')
       {
           steps
          {
            deploy adapters: [tomcat9(credentialsId: '3ffa97a9-5c9c-465e-be1e-b31a7f5b2d0a', path: '', url: 'http://172.31.47.228:8080')], contextPath: 'mytestapp', war: '**/*.war'
          }
       }
    stage('ContinuousTesting')
       {
           steps
          {    
            git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
          }
       } 
   
    stage('ContinuousDelivery')
       {
           steps
          {
           input 'need approval from manager'
           deploy adapters: [tomcat9(credentialsId: '3ffa97a9-5c9c-465e-be1e-b31a7f5b2d0a', path: '', url: 'http://172.31.43.171:8080')], contextPath: 'prodapp', war: '**/*.war'
          } 
       }
      
   }
}



