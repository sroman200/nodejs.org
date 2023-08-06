pipeline {
    agent none
    options {
        // This is required if you want to clean before build
        skipDefaultCheckout(true)
    }
    environment {
      //CRED      = credentials('key-slave')
      BUILD_DIR = "{JENKINS_HOME}/workspace/nodejs/build"
      
      //HOME_DIR  = "/home/centos/jenkins/"
    }
     stages {
       
        stage("Env Variables") {
           agent {label 'slave'}
            steps {
                sh 'printenv'
                //cleanWs()
            }
        }
    
        stage('check directory BUILD') { //----------------
          agent {label 'slave'}
          when {
            expression {
              return fileExists("${BUILD_DIR}")
              }
            } 
          steps {
             echo "${BUILD_DIR} exists" 
            }
        } //stage check 
        stage('list') { //----------------
          agent {label 'slave'}
          steps{
            sh 'pwd && ls -lat'
                /* "-------------GIT CLONE" */
            script {
                         git credentialsId: 'github', url: 'git@github.com:sroman200/nodejs.org.git'
                         // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
                         sh "ls -lart" 
                         // List all branches in your repo. 
                         sh "git branch -a"
            }
          } 
       }//stage list
       
     }   //stages
} // pipline
