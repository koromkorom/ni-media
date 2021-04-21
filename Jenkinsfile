pipeline {

  agent any
  
  stages {
  
    stage("build") {
      steps {
        echo 'building the application'
        //runCommand( 'cmake -E remove_directory build')                             // make sure the build is clean
        runCommand( 'cmake -B build ')
        runCommand( 'cmake --build build')
            
        echo '----- CMake project was build successfully -----'
        }
    }
    
    stage("test") {
      steps {
        echo 'testing the application'
        runCommand( 'ctest --test-dir build')
        }
    }
    
    stage("deploy") {
      steps {
        echo 'deploying the application'
        }
    }


  }
}

def runCommand( command )
{
    if(isUnix())
    {
        sh command
    }
    else
    {
        bat command
    }
}