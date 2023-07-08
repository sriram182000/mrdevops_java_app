@Library('jenkins-shared-library') _
pipeline {
    agent any 

    stages{

        stage('Git checkout') {
           
            steps {
                   
                    gitcheckout(
                        branch: "main",
                        url: "https://github.com/sriram182000/mrdevops_java_app.git"
                    )
            }
        }
    }
}