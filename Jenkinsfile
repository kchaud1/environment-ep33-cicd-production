@Library('shared-library@main') _
pipeline{
    
    agent any
    
    /*tools {
         maven 'maven'
         jdk 'java'
    }*/

    stages{
        
        stage('checkout'){
          
            steps{
                
                  script{
    def browsers = ['chrome', 'firefox']
    def map = [:]
    }
                
                //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
            cleanWs()
            runGitCheckOut(false)
                echo "Git URL is ${GIT_URL}" 
            script{
                def url = scm.getUserRemoteConfigs()[0].getUrl()-"https://"
                echo "Git URL is ${url}"
                def config = [:]
                config = pipelineSetup()}
            }
        }
       
        stage('build'){
            steps{
               sh 'mvn clean install'
            }
        }
    }
}
