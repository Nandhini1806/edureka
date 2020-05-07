pipeline{
  agent any
  stages{
    stage('one'){
      steps{
      echo "executing first step"
      }  
    }
    stage('two'){
      steps{
        input("Do you want to proceed?")
      }
    }
    stage('three'){
      when{
        not{
          branch "master"
        }
      }
      steps{
        echo "hello"
      }
    }
    stage('four'){
      parallel{
        stage('Unit test'){
          steps{
            echo "unit test done"
          }
        }
        stage('integration test'){
          agent{
            docker{
              docker pull ubuntu:14.04
            }
          }
          steps{
            echo "integration test done"
          }
        }
      }
    }
  }
}
      
