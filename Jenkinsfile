@Library('jenkins-shared-library') _
pipeline {
    agent any 
    tools {
        maven 'Maven3'
    }
    parameters {
        choice(name:'action',choices:"create\ndestroy",description:"create or destroy")
    }
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    gitcheckout(
                        branch:"main",
                        url:"https://github.com/sriram182000/mrdevops_java_app.git"
                    )
                }
            }
        }

        stage('Maven Unit Testing') {
            when{expression {params.action=='create'}}
            steps {
                script {
                    UnitTest()
                }
            }
        }

        stage('Maven Integration Test') {
            when {expression{params.action=='create'}}
            steps {
                script {

                    IntegrationTest()

                }
            }
        }

        stage("Maven Build") {
            when {expression{params.action=='create'}}
            steps {
                script {
                    MavenBuild()
                }
            }
        }
    }
}