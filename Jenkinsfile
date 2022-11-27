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
            sh 'pwd && ls -lat'
          } 
       }//stage list
       
     }   //stages
} // pipline
