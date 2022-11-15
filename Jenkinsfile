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
                
               
                
                //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
            cleanWs()
            runGitCheckOut(false)
                echo "Git URL is ${GIT_URL}" 
            script{
                def url = scm.getUserRemoteConfigs()[0].getUrl()-"https://"
                echo "Git URL is ${url}"
                sh(returnStdout:  true, script: "git tag --sort=-creatordate | head -n 1").trim()
                def config = [:]
                config = pipelineSetup()
            echo "${config}"
                            def deployUrl = config['rtDeploy']
                    echo "${deployUrl}"}
                def deployU = config['rtDeploy']
                echo "${config}"
                //sh "${args}"
                //def service_name = ['my-service']
                //runDockerBuild.build(config, service_name)
                  //  runDockerPush(config, service_name)
            }
            
            
        }
       
        stage('build and upload'){
            steps{
                //sh "mvn clean install"
                

                script{
                 
                def config = [:]
                    config = pipelineSetup()
                    def service_name = ['my-service']
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
                    
                    runDockerBuild.build(config, service_name)
                    runDockerPush(config, service_name)
                
                }
            }
        }
    }
}
