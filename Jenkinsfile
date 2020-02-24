pipeline {
    libraries{
     lib 'shlib'
}
    agent any
    stages{
    /*tools {
        maven "Maven"   
    } */  
  /*  environment{
        sonarscanner = tool 'SonarScanner'
    }*/
  /*  stages {
        stage('Compile-Build-Test ') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('azure'){
            steps{
                //   withCredentials([string(credentialsId: 'azure')]){
                 sh 'az extension add --name azure-devops'
               // sh 'curl -u vickysastry.vs@outlook.com:zsxapkj3zwk6rtz7zm4tyli7ayk7yt5yehp5ic7erlec4xsf7tya --request POST https://dev.azure.com/vickysastryvs/_apis/projects?api-version=5.1'
               // sh 'az devops project create --name vicky --organization https://dev.azure.com/vickysastryvs'
                sh 'az login --allow-no-subscriptions'
                
                sh 'az devops project list --organization https://dev.azure.com/vickysastryvs'
                
            }
        }     
       */ 
        //}
   /* stage('store output'){
        steps{
           sh '''
               sudo curl  --request GET 'https://dev.azure.com/vickysastryvs/_apis/projects/abcdef1?api-version=5.1' \
                     --header 'Accept: application/json' \
                     --header 'Authorization: Basic dmlja3lzYXN0cnkudnNAb3V0bG9vay5jb206enN4YXBrajN6d2s2cnR6N3ptNHR5bGk3YXlrN3l0NXllaHA1aWM3ZXJsZWM0eHNmN3R5YQ==' -o out.json
           '''
        }
    }*/
        stage('azureconnector')
        {
            steps
            {
                fff()
            }
        }
        /*stage('deleteteam')
        {
            steps
            {
                delete_team()
            }
        }*/
      /*  stage('azurecollector')
        {
            steps
            {
                azurecol()
            }
        }*/
        
      /*  stage('sonarconnector')
        {
            steps
            {
                sonarConnector()
            }
        }
        
        stage('sonarcollector')
        {
            steps
            {
                sonarCollector()
            }
        }
        
       */
        
        
        /*stage('azure'){
            steps{
             /*  sh 'curl -u vickysastry.vs@outlook.com:zsxapkj3zwk6rtz7zm4tyli7ayk7yt5yehp5ic7erlec4xsf7tya --request DELETE https://dev.azure.com/vickysastryvs/d2/_apis/build/definitions/1?api-version=5.0'
            
                sh 'curl -u vickysastry.vs@outlook.com:zsxapkj3zwk6rtz7zm4tyli7ayk7yt5yehp5ic7erlec4xsf7tya --request GET https://dev.azure.com/vickysastryvs/_apis/projects?api-version=5.1'
               /* sh 'curl -u vickysastry.vs@outlook.com:zsxapkj3zwk6rtz7zm4tyli7ayk7yt5yehp5ic7erlec4xsf7tya -H -X POST https://dev.azure.com/vickysastryvs/d2/_apis/build/builds?sourceBuildId=3&api-version=5.1'
            
                sh '''
                curl --location --request POST 'https://dev.azure.com/vickysastryvs/_apis/projects?api-version=6.0-preview.4' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'Authorization: Basic dmlja3lzYXN0cnkudnNAb3V0bG9vay5jb206enN4YXBrajN6d2s2cnR6N3ptNHR5bGk3YXlrN3l0NXllaHA1aWM3ZXJsZWM0eHNmN3R5YQ==' \
--data-raw '{
  "name": "${name}",
  "description": "Testing for Project creation using curl",
  "capabilities": {
    "versioncontrol": {
      "sourceControlType": "Git"
    },
    "processTemplate": {
      "templateTypeId": "6b724908-ef14-45cf-84f8-768b5384da45"
    }
  }
}'
'''
            }
        
       }
          */
        /*stage('SonarQube Analysis'){
            steps{
               withSonarQubeEnv('sonarqube'){
                     sh '${sonarscanner}/bin/sonar-scanner -Dproject.settings=./sonar-project.properties'
                }
            }
        }
        stage("Quality Gate") {
            steps {
              timeout(time: 3, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
        }
        stage('Pushing to Nexus'){
            steps{
               withCredentials([usernamePassword(credentialsId: 'nexus-credentialss', passwordVariable: 'password', usernameVariable: 'username'),string(credentialsId: 'NEXUS_URL', variable: 'nexus_url')]){
                    //sh 'curl -u ${username}:${password} --upload-file target/BMIBeta-${BUILD_NUMBER}.jar http://18.224.155.110:8081/nexus/content/repositories/devopstraining/comrades/BMI-${BUILD_NUMBER}.war'
                   sh 'curl -v -F file=@target/BMI-0.war -u ${username}:${password} http://${nexus_url}/nexus/content/repositories/devopstraining/comrades/bmi/BMI/BMI-${BUILD_NUMBER}.war'
               }
            }
        }
        stage('Uploading yml to Ansible'){
            steps{
                withCredentials([string(credentialsId: 'ANSADMIN_PASSWORD', variable: 'ansadmin_password')]){
                //sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'project-ansible.yml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])   
                sh 'sshpass -p ${ansadmin_password} scp -v project-ansible.yml ansadmin@172.31.22.13:/opt/playbooks'
                }
            }
            
        }
        stage('Uploading artifacts to Ansible'){
            steps{
                withCredentials([string(credentialsId: 'ANSADMIN_PASSWORD', variable: 'ansadmin_password')]){
                //sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /opt/playbooks/project-ansible.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '/target/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
                //sh 'scp -v -i /home/ansadmin/.ssh/jen-ans.pub -o StrictHostKeyChecking=no target/*.war ansadmin@172.31.22.13:/opt/playbooks/target'
                //sh 'sshpass -p ${ansadmin_password} scp -v target/*.war ansadmin@172.31.22.13:/opt/playbooks/target'
                sh 'sshpass -p ${ansadmin_password} ssh -v -o StrictHostKeyChecking=no ansadmin@172.31.22.13 \"cd /opt/playbooks/target; wget -O BMI.war http://18.224.155.110:8081/nexus/content/repositories/devopstraining/comrades/bmi/BMI/BMI-${BUILD_NUMBER}.war\"'
                }
            }
        }
       stage('Executing Playbook'){
            steps{
                withCredentials([string(credentialsId: 'ANSADMIN_PASSWORD', variable: 'ansadmin_password')]){//-C \"export VAULTPASS=${ansadmin_password};
                    sh 'sshpass -p ${ansadmin_password} ssh -v -o StrictHostKeyChecking=no ansadmin@172.31.22.13  \"ansible-playbook /opt/playbooks/project-ansible.yml\"'
                    //sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible_server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /opt/playbooks/project-ansible.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
                }
            }
        }
        
        /*stage('Deployment to AWS'){
            steps{
            withCredentials([usernamePassword(credentialsId: 'tomcatCredentials', passwordVariable: 'password', usernameVariable: 'username'),string(credentialsId: 'TOMCAT_URL', variable: 'tomcat_url')]){
                    sh 'curl ${tomcat_url}/manager/text/undeploy?path=/BMI -u ${username}:${password}'
                    sh 'curl -v -u ${username}:${password} -T target/BMI${BUILD_NUMBER}.war ${tomcat_url}/manager/text/deploy?path=/BMI'
                }
            }
        }
        
     }
               post { 
                success { 
                    echo 'notified to slack '
                    slackSend (color: '#00FF00', message: " JOB SUCCESSFUL: Job '${JOB_NAME} [${BUILD_NUMBER}]' (${BUILD_URL})")
                }
                failure {
                    echo 'notified to slack'
                    slackSend (color: '#FF0000', message: " JOB FAILED: Job '${JOB_NAME} [${BUILD_NUMBER}]' (${BUILD_URL})")
                }
               */
    }

}
