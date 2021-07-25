pipeline {
    agent any  
    
    tools
    {
       maven "MAVEN_HOME"
    }    
    
  stages {
    stage('Execute Maven') {
  		   steps { 			 
  				sh 'mvn clean package'             
  		  }
    }
    stage('Ansible Deploy') {
  			steps {
          ansiblePlaybook become: true, credentialsId: 'vagrant', disableHostKeyChecking: true, installation: 'Ansible', playbook: 'my_play.yml'
  			}
    }
  }
}
