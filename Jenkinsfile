/*
This pipeline will carry out the following on the project:

1. Git secret checker
2. Software Composition Analysis
3. Static Application Security Testing
4. Container security audit 
5. Dynamic Application Security Testing
6. Host system security audit
7. Host application protection

*/

testenv = "null"

pipeline {
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
