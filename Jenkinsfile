pipeline {
    agent none
    environment {
      branch     = "v0.2-rc"
      new_branch = false
      CRED      = credentials('key-slave')
      BUILD_DIR = "/home/centos/jenkins/nodejs.org/build"
    }
     stages {
        stage('Build') { //----------------
          agent {label 'slave'}
            steps {
                script {
                  if ( [ -d "$BUILD_DIR" ]) 
                    echo "$BUILD_DIR does exist."
                  else  {
                         /* "-------------GIT CLONE" */
                         git credentialsId: 'key-slave', url: 'git@github.com:sroman200/nodejs.org.git'
                         // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
                         sh "ls -lart ./*" 
                         // List all branches in your repo. 
                         sh "git branch -a"
                    
                    
                         //sshagent( ['key-git'] ) {
                         //sh ("git push --set-upstream origin ${branch}${num+1}")
                         // }
                        /* "//------------ end PUSH" */
                    } 
                }    //- main script
            } // steps 1
        } //stage Build 
     }   //stages
} // pipline
