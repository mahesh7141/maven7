pipeline {
    agent any

    stages {
        stage('continousdownload') 
        {
            steps 
            {
                 git 'https://github.com/mahesh7141/maven7.git'
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
                   sh 'scp /var/lib/jenkins/workspace/declarativepipeline1/webapp/target/webapp.war ubuntu@172.31.4.221:/var/lib/tomcat9/webapps/testwebapp.war'
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
         sh 'scp /var/lib/jenkins/workspace/declarativepipeline1/webapp/target/webapp.war ubuntu@172.31.3.58:/var/lib/tomcat9/webapps/prodwebapp.war'
        
            }
            
       
        }
    }
}

