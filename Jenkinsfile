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



       }
 }

