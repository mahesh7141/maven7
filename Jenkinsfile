pipeline {
    agent any

    stages {
        stage('continousdownload') 
        {
            steps 
            {
                 git 'https://github.com/mahesh7141/maven7.git':
            }
        }
        
         stage('continousbuild') 
        {
            steps 
            {
                  sh 'mvn package'
            }
        }
        
         stage('continousdeployment') 
        {
            steps 
            {
                  deploy adapters: [tomcat9(credentialsId: 'b86ca0a2-a6bc-4ff8-9a71-388380544eb9', path: '', url: 'http://172.31.10.23:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        
         stage('continoustesting') 
        {
            steps 
            {
                 git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                 
                 sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline1/testing.jar'
                 
        
            }
            
       
        }
        
         stage('continousdelivery') 
        {
            steps 
            {
                input message: 'need approval from dm! ', submitter: 'routhu'
         deploy adapters: [tomcat9(credentialsId: 'b86ca0a2-a6bc-4ff8-9a71-388380544eb9', path: '', url: 'http://172.31.10.73:8080')], contextPath: 'myprodapp', war: '**/*.war'
                 
        
            }
            
       
        }
    }
}

