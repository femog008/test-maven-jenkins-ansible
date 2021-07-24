pipeline {
    agent any  
    
    tools
    {
       maven "MAVEN_HOME"
    }    
    
  stages {
    stage('Tools Init') {
        steps {
            script {
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"
             def tfHome = tool name: 'Ansible'
              env.PATH = "${tfHome}:${env.PATH}"
               sh 'ansible --version'
                
          }
        }
    }
    stage('Execute Maven') {
  		   steps { 			 
  				sh 'mvn package'             
  		  }
    }
    stage('Ansible Deploy') {
  			steps {
          ansiblePlaybook become: true, credentialsId: 'Femog008', disableHostKeyChecking: true, installation: 'Ansible', playbook: 'my_play.yml'
  			   #sh "ansible-playbook main.yml -i inventories/dev/hosts -- user jenkins --key-file ~/.ssh/id_rsa"
  			}
    }
  }
}
