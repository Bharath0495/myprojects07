pipeline{

  tools{
     jdk 'myjava'
     maven 'mymaven'
}



agent any

stages{

   stage('Clone repo')
    {
      steps{
           
        git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'

               }

    }

 stage('Compile the code')
    {
      steps{
           
      sh 'mvn compile'

               }

    }

 stage('Code Review')
    {
      steps{
           
      sh 'mvn pmd:pmd'

               }

    }


 stage('test the code')
    {
      steps{
       echo 'Testing'    
      sh 'mvn test'


               }
      
       post{

       success{
                    junit 'target/surefire-reports/*.xml'
               }
                }
    }

 stage('Coverage of the code')
    {
      steps{
        
      sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'


               }
      
       post{

       success{
                    cobertura autoUpdateHealth: false, autoUpdateStability: false, coberturaReportFile: 'target/site/cobertura/coverage.xml', conditionalCoverageTargets: '70, 0, 0', failUnhealthy: false, failUnstable: false, lineCoverageTargets: '80, 0, 0', maxNumberOfBuilds: 0, methodCoverageTargets: '80, 0, 0', onlyStable: false, sourceEncoding: 'ASCII', zoomCoverageChart: false
               }
                }
    }


 stage('Package the code')
    {
      steps{
           
      sh 'mvn package'

               }

    }

}
}
