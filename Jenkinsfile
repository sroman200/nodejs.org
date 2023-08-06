pipeline {
    agent none
    
    environment {
      //CRED      = credentials('key-slave')
      BUILD_DIR = "{JENKINS_HOME}/workspace/nodejs/build"
      
      //HOME_DIR  = "/home/centos/jenkins/"
    }
     stages {
        stage("Env Variables") {
            steps {
                sh "printenv"
                echo "${JENKINS_HOME}   root"
                echo "${ITEM_ROOTDIR}   build"
                echo "${ITEM_FULLNAME}   full_path"
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
