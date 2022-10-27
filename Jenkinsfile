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
                config = pipelineSetup()
            echo "${config}"
                            def deployUrl = config['rtDeploy']
                    echo "${deployUrl}"}
                //echo "${config}"
            }
        }
       
        stage('build and upload'){
            steps{
               sh 'mvn clean install'
                script{
                 
                def config = [:]
                    config = pipelineSetup()
                def aid = utilMaven.getArtifactID()
                def path = utilMaven.getArtifactoryPath()
                echo "${aid}"
                echo "${path}"
                def gid = utilMaven.getGroupID()
                echo "${gid}"
                def version = utilMaven.getVersion()
                echo "${version}"
                def deployUrl = config['rtDeploy']
                    echo "${deployUrl}${path}/${aid}/${version}"
                    runDockerBuild.build(config, serviceNames=['karan'])
                
                }
            }
        }
    }
}
