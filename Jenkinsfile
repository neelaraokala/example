pipeline {
    agent any
    tools {
        go 'go1.14'
    }
    environment {
        GO114MODULE = 'on'
        CGO_ENABLED = 0 
        GOPATH = "/usr/local/go/bin"
    }
    stages {        
        stage('Pre Test') {
            steps {
           
                sh 'go version'
            
            }
        }
        
        stage('Build') {
            steps {
                
                echo 'Compiling and building'
                sh 'go build'
            }
        }

        stage('Test') {
            steps {
                withEnv(["PATH+GO=${GOPATH}/bin"]){
                    echo 'Running vetting'
                    sh 'go vet .'
                    echo 'Running linting'
                    sh 'golint .'
                    echo 'Running test'
                    sh 'cd test && go test -v'
                }
            }
        }
        
    }
      
}
