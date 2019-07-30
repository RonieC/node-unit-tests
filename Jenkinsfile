pipeline {
    agent none
    options {
        buildDiscarder logRotator(daysToKeepStr: '8', numToKeepStr:'5')
    }


environment {
    MyKeyId="RCD"
}

stages {
    stage('Downloading source code') {
        // when{
        //     branch "master"
        // }
        steps{
            script{
                node{
                    println "\n My first Stage.\n MyKeyId value is ${MyKeyId}\n"
                }
            }
        }
    }
    
    stage('test') {
        steps{
            script{
                node {
                    println "\n My first Stage.\n MyKeyId value is ${MyKeyId}\n"
                }
            }
        }
    }
    
}
}