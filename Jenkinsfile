

testenv = "null"

pipeline {
            agent any
            stages { 
            stage("Checkout Code") {
              steps {
                script {
                  git branch: "master",
                    credentialsId: 'my-credentials',
                    url: 'https://user@github.org/myproject/sample-repo.git'
            }
        }
    }
}
}
