pipeline {
    agent none
    environment {
      //CRED      = credentials('key-slave')
      BUILD_DIR = "/home/centos/jenkins/nodejs.org/build"
      //HOME_DIR  = "/home/centos/jenkins/"
    }
     stages {
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
            //sh 'pwd && ls -lat'
                /* "-------------GIT CLONE" */
            script {
                         git credentialsId: 'key-git', url: 'git@github.com:sroman200/nodejs.org.git'
                         // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
                         sh "ls -lart ./*" 
                         // List all branches in your repo. 
                         sh "git branch -a"
            }
          } 
       }//stage list
       
     }   //stages
} // pipline
