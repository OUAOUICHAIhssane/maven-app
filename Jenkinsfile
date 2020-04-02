pipeline{
agent any
        tools{
        maven 'apache-maven-3.6.3'
        jdk 'jdk1.8.0_231'
        }
        stages{
                stage('build'){
                                steps{
                                bat 'mvn compiler:complie'
                                }
                                post {
                    success {
                     bat "echo 'projet compilé avec succès'"
                    }
                     failure {
                      bat "echo 'Erreur lors de la compilation du projet'"
                     }
               }
                 }
                 stage('test') {
              steps {
                 bat 'mvn test'
             }
             post {
                 always {
                     junit 'target/surefire-reports/*.xml'
                 }
             }
       }
                stage('couverture') {
            steps{
                 
                bat 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
           }
           post {
                always {
                      cobertura coberturaReportFile: '**/target/site/cobertura/coverage.xml'
                     
                       }
               }
  }
  }                 
