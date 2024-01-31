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
            deploy adapters: [tomcat9(credentialsId: 'cbc933d1-a8ae-48a1-a14e-cc3a5f0df3d0', path: '', url: 'http://172.31.19.226:8080')], contextPath: 'testapp1', war: '**/*.war'
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
                  deploy adapters: [tomcat9(credentialsId: 'cbc933d1-a8ae-48a1-a14e-cc3a5f0df3d0', path: '', url: 'http://172.31.19.226:8080')], contextPath: 'prodapp1', war: '**/*.war'
          } 
       }
      
   }
}



