pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }
	
	stage('ServiceAccount') {
	   steps { sh ''' oc adm policy add-role-to-user edit system:serviceaccount:yfbzrr-jenkins:jenkins ''' }
				}
        stage('Release'){
	   steps { sh ''' oc start-build greeting-console --follow --wait ''' }
      			}
    }
}
