// flask uruchomiony z linii poleceń

pipeline {
    agent any
    
    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }        }
        
        stage('Run with venv') {
            options {
                timeout(time: 2, unit: 'MINUTES') 
            }

            steps {
                script {
                    sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                    python3 app.py// flask uruchomiony z linii poleceń

pipeline {
    agent any
    
    
    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Run with venv') {
            options {
                timeout(time: 1, unit: 'MINUTES') 
                }

            
            steps {
                script {
                        sh '''
                        python3 -m venv venv
                        . venv/bin/activate
                        pip install -r requirements.txt
                        python3 app.py
                        '''
                }
            }
        }
    
        
        
    }
    
   // abort zmieniamy w sukces na końcu
   post {
    aborted {
      script {
        // jeśli chcesz traktować timeout/abort jako sukces
        currentBuild.result = 'SUCCESS'
      }
    }
  }
   
   
}
                    '''
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
                sh 'sleep 5'
                sh 'curl -f http://localhost:5000 || exit 1'
            }
        }
    }
}
