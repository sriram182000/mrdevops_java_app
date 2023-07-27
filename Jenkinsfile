@Library('jenkins-shared-library') _
pipeline {
    agent any 
    tools {
        maven 'Maven3'
    }
    parameters {
        choice(name:'action',choices:"create\ndestroy",description:"create or destroy")
       // string(name:'Imgname', description:'docker image name',defaultValue:"Javaapp")
        //tring(name:'Dockerhub',description:'docker hub account name',defaultValue: "sriram789")
       // string(name:'Tagname',description:"tagname of image",defaultValue:"latest")
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
            }b
        }

       stage('Maven Integration Test') {
           when {expression{params.action=='create'}}
            steps {
                script {
                       IntegrationTest()

                }
            }
        }

        stage ('Static Code Analysis') {
            steps {
                script {
                    def sonar='sonar'
                    StaticCodeAnalysis(sonar)
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

       // stage("Docker Build") {
          //   when {expression{params.action=='create'}}
             //steps {
                    // script {
                    //DockerBuild("${params.Dockerhub}","${params.Imgname}","${params.Tagname}")
                //}
            //}
        //}
        //stage ("Docker Push") {
          //  when {expression{params.action=='create'}}
            //steps{
              //  script {
                //    DockerPush("${params.Dockerhub}","${params.Imgname}","${params.Tagname}")
                //}
            //}
        //}
    }
}