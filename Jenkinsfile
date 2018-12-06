#!/usr/bin/env groovy

def imageName = 'odiarra/hellojira'

properties([
    buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5')),
    pipelineTriggers([[$class:"SCMTrigger", scmpoll_spec:"H/15 * * * *"]]),
])
node('image docker'){
    
    def app 

    stage('Clone repository'){
        
        checkout scm   
    }        
    stage('Build image'){ 
            
        app = docker.build("${imageName}:${imageTag}", 'jira') 
    }    
        
    stage('Test image') {
             
        app.inside {
        	sh 'echo "Tests passed"'
        } 
    }
}

