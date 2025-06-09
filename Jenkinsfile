pipeline{
  agent any
  environment{
    LANG='en_US.UTF-8'
    LC_ALL='en_US.UTF-8'
  }
  tools{
    maven 'Maven'
  }
  stages{
    stage('Chechout'){
      steps{
        git branch:'master',url:'https://github.com/VinayLR15/Ansible2-CICD.git'
      }
    }
      stage("Build"){
        steps{
          sh 'mvn clean package'
        }
      }
        stage('Archive'){
          steps{
            archiveArtifacts artifacts:'target/*.war',fingerprint:true
          }
        }
    stage('Deploy'){
      steps{
        sh 'mvn clean package'
        sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
      }
    }
  }
}
