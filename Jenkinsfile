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
                step([$class: 'WsCleanup'])
                checkout scm
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
          } 
       }//stage list
        
        stage('Build') { //----------------
          agent {label 'slave'}
          steps{
                  nodejs(nodeJSInstallationName: 'nodejs16') {
                   sh 'npm -v'  //substitute with your code
                   sh 'node -v'
                   
                   
                   // #build 'deploy-14' ## если нужно 
                   
                   
                   git branch: 'main', url: 'https://github.com/nodejs/nodejs.org.git'
                   sh """ 
                   
                   cd $WORKSPACE && \
                   npm install && npm run build && \
                   ls -la build
                   
                   """
             }
          }   
       }//stage build       
     }   //stages
} // pipline
