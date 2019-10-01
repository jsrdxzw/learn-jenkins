pipeline {
   agent any
   stages {
     stage('build'){
       echo 'build stage'
     }
     post {
       always {
        echo 'stage post always'
       }
     }
   }
   post{
    changed{
     echo 'pipeline post changed'
    }
    always{
     echo 'pipeline post always'
    }
    success{
     echo 'pipeline post success'
    }
   }
}