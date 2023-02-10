pipeline{

agent any

stages {

    stage('Git Checkout'){

        steps{
               git branch: 'main', url: 'https://github.com/vineshbagul/newprojectofgitflow.git'
            }
        }

         stage('UNIT Testing'){

                    steps{
                           bat 'mvn test'
                        }
                    }

            stage('Integration Testing'){

                          steps{
                              bat 'mvn verify -DskipUnitTests'
                                      }
                                  }

             stage('Maven Build'){

                                steps{
                                   bat 'mvn clean install'
                                          }
                                       }
                stage('Static code analysis'){

                                         steps{
                                            script {
                                              withSonarQubeEnv(credentialsId: 'sonar-api') {
                                                    bat 'mvn clean package sonar:sonar '
                                                        }
                                                  }
                                             }
                                             }

                 stage('Quality gate Status'){
                  steps{
                   script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api'
                    }
                  }
                 }

                 stage('Upload war file to nexus'){
                 steps{
                    def readPomVersion = readMavenPom file: 'pom.xml'
                    script {
                      nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Uber.jar', type: 'jar']], credentialsId: 'nexus-auth', groupId: 'com.example', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'demoapp-release', version: 'readPomVersion.version'
                      }
                 }
                 }


   }
}

