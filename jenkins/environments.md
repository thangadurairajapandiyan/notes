# Jenkins Environments

* To see all jenkins pre-defined variables, `https://ip-address:8080/env-vars.thml`
* To print all environment variables
  ```
  sh "printenv | sort"
  ```
* Using env variables
  ```
  // ${env.BUILD_NUMBER} or ${BUILD_NUMBER} are same
  echo "BUILD_NUMBER = ${env.BUILD_NUMBER}"
  // If you are sh block you access variable directly like this $BUILD_NUMBER
  sh 'echo BUILD_NUMBER = $BUILD_NUMBER'
  ```
* Setting env variables. All the environment variables are casted to string
  * Environment in pipeline block (Accessible to all stages)
    ```
    pipeline {
      agent any
      environment {
          USER_NAME = "vignesh"
          USER_ID = 23 // All the environment variable are casted to string
      }
    }
    ```
  * Environments at stage level (only accessible to that stage)
    ```
    stage ("Using environment variable") {
      environment {
          USER_PATH = "/home/vignesh"
      }
      steps {
          echo "USER_PATH = ${env.USER_PATH}"
      }
    }
    ```
  * Using script block inside the stage
    ```
    stage ("Using environment variable") {
      steps {
          script {
              env.USER_GROUP = "users"
          }
          echo "USER_GROUP = ${env.USER_GROUP}"
      }
    }
    ```
  * Using withEnv inside the stage
    ```
    stage ("Using environment variable") {
      withEnv(["USER_PSD=secret", "USER_ID_ADMIN=false"]) {
          echo "USER_PSD = ${USER_PSD}"
          sh 'USER_ID_ADMIN = $USER_ID_ADMIN'
      }
    }
    ```
* Overriding env variables
  * we can override the environments in pipeline environment block with the environments defined in stage environment block
    ```
    pipeline {
        agent any
        environment {
            USER_NAME = "vignesh"
            USER_ID = 23 // All the environment variable are casted to string
        }
        stage ("Using environment variable") {
            environment {
                USER_NAME = "venkatesh"
            }
            steps {
                echo "USER_NAME = ${env.USER_NAME}" //Now the USER_NAME value is venkatesh only in this stage, outside the stage the value will be from pipeline                   environment block
            }
        }
        stage ("Accessing environment variables") {
            steps {
                sh 'echo USER_NAME = $USER_NAME' // Here the value is 'vignesh' from pipeline environment block
            }
        }
    }
    ```
  * Overriding the value in script block **will not have any effect**
    ```
    
    ```
  
