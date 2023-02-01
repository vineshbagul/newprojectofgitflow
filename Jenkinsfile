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

       }
 }

