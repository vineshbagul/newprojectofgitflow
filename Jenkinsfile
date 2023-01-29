pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                   git branch: 'main', url: 'https://github.com/vineshbagul/newprojectofgitflow.git'
                }
            }
             stage('UNIT testing'){

                        steps{

                                sh 'mvn test'
                            }

                    }


             }

     }
