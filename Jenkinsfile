pipeline {
  agent any
  tools { 
        maven 'maven3'  
    }
   stages{
    stage('Checkout') {
            steps {
                git 'https://github.com/your-repo/your-node-app.git'
            }
        }
    stage('Build') {
            steps {
                sh 'mvn install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
