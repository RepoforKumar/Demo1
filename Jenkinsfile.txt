pipeline{
  // any available server where jenkins pipeline can run
 // current server is available, so pipeline will run on it.
 agent any
 tools{
     maven 'mymaven'
 }
stages{
    stage('Clone Code'){
        steps{
           git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
        }
    }
    stage('CodeReview'){
        steps{
            sh 'mvn pmd:pmd'
        }
    }
    stage('Compile Code'){
        steps{
          sh  'mvn compile'
        }
    }
    stage('Test Code')
    {
        steps{
            sh 'mvn test'
        }
    }
    stage('Package Code')
    {
        steps{
            sh 'mvn package'
        }
    }
}
 
 
}
