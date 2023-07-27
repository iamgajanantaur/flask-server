pipeline {
    agent any
    stages {
        stage ('SCM Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/iamgajanantaur/flask-server.git'
        
            }
        }
        
        stage ('docker image build') {
            steps {
                sh '/usr/bin/docker build -t iamgajanantaur/flask-server .'    
            }
        }
        
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_PXvEcCymwr8n44zqRx6Z6buzk6g | /usr/bin/docker login -u iamgajanantaur --password-stdin'
            }
        }
        
        stage ('docker push') {
            
            steps {
                sh '/usr/bin/docker image push iamgajanantaur/flask-server'
            }
        }
        
        stage ('user input') {
            
            steps {
                input 'Are you sure? You want to deploy.'
            }
        }
        
        stage ('existings service remove') {
            steps {
                sh '/usr/bin/docker service rm service1'
            }
        }
        
        stage ('start sevice') {
            steps {
                sh '/usr/bin/docker service create --name service1 -p 4000:4000 --replicas 2 iamgajanantaur/flask-server'
            }
        }
        
        
    }
    
}
