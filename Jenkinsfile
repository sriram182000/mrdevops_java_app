@Library('jenkins-shared-library') _
pipeline {
    agent any 
     tools {
        maven "Maven3"
    }
    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'ImgName', description:'name of the image', defaultValue: 'javaapp')
        string(name: 'ImgTag', description:'name of the tag', defaultValue:'v1')
        string(name: 'DockerHubUser', description: "username of dockerhub", defaultValue: 'sriram789')
    }

    stages{

        stage('Git checkout') {
        when { expression{ params.action=='create'}}
           
            steps {
                gitCheckout(
                        branch: "main",
                        url: "https://github.com/sriram182000/mrdevops_java_app.git"
                )
            }
        }
        stage('Unit Testing') {
            when {expression{params.action=='create'}}
            steps {
                script {
                    mvnunittest()
                }
            }
        }
        stage ('Integration Testing') {
            when{expression{params.action=='create'}}
            steps {
                script {
                    mvninttest()
                }
            }
        }
        stage ('Maven Build') {
            when {expression {params.action=='create'}}
            steps {
                script {
                    mvnBuild()
                }
            }
        }
        stage('DOcker build') {
            when{expression{params.action=='create'}}
            steps {
                script {
                    dockerBuild("${params.ImgName}","${params.ImgTag}","${params.DockerHubUser}")

                }
            }     
        }
    }
}