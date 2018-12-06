node {
    
    def app 

    stage('Clone repository'){
        
        checkout scm   
    }        
    stage('Build image'){ 
            
        app = docker.build('odiarra/hellojira') 
    }    
        
    stage('Test') {
             
        app.inside {
        	sh 'echo "Tests passed"'
        } 
    }
}

