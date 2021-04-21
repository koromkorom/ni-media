pipeline {

  agent any
  
  stages {
  
    stage("build") {
      steps {
        echo 'building the application'
        cmakeBuild(installation: 'InSearchPath')
        }
    }
    
    stage("test") {
      steps {
        echo 'testing the application'
        ctest(installation: 'InSearchPath')
        }
    }
    
    stage("deploy") {
      steps {
        echo 'deploying the application'
        }
    }
  }
}