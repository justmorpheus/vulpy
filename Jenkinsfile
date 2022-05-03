

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
        sh 'docker rmi gesellix/trufflehog:latest'
        sh 'docker run gesellix/trufflehog --json https://github.com/justmorpheus/vulpy.git > trufflehog'
        sh 'cat trufflehog'
      }
    }
            
            }      
}
