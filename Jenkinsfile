

testenv = "null"

pipeline {
            agent any
            stages { 
            stage('Installing Dependency') {
            steps {
                script {
                    sh 'python3 -m pip install -U pip setuptools'
                    sh 'python3 -m pip install -r requirements.txt'
                            dir("bad") {
                                        sh 'ls -la'
                                        sh 'chmod +x db_init.py'
                                        sh './db_init.py'
                     }
                    
                }
            }
        }
                                      
    stage ('Check Git Secrets') {
      steps {
        echo 'Running trufflehog to check project history for secrets'
        sh 'rm trufflehog || true'
        sh 'docker rmi -f gesellix/trufflehog:latest  || true'
        sh 'docker run gesellix/trufflehog --debug --json https://github.com/justmorpheus/vulpy.git > trufflehog'
        sh 'cat trufflehog'
      }
    }
           stage ('Build & Deploy') {
      steps {
        echo 'Deploy the python application'
        sh 'python3 vulpy.py '

      }
    }
                        
            
 }      
}
