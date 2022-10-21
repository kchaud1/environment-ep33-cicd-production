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
    def config = [:]
    }
                
                //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
            cleanWs()
            runGitCheckOut(false)
            script{
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
