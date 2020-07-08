pipeline {
    agent any
   
    environment{
        sonarscanner = tool 'sonar'
    }
    stages {
	    //stage('remove'){
		 
        stage('build') {
            
		   agent {
			   docker { image 'sumavarshitha/java-maven-node' }}
		steps {
			sh 'rm -rf BMIbeta' 
	        sh 'git clone https://github.com/SumaVarshitha/BMIbeta.git'
                sh "mvn clean package"
            
	    }
        }
        stage('SonarQube Analysis'){
            steps{
               withSonarQubeEnv('SonarQube'){
                     sh '${sonarscanner}/bin/sonar-scanner -Dproject.settings=./sonar-project.properties'
                }
            }
        }

    }
        
      /*  stage("Quality Gate") {
            steps {
              timeout(time: 3, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
        }*/
       
}
          
