node('master') {
	stage('ContinuousDownload') {
		git 'https://github.com/rajeshr82/sprintboot-demo.git'
	}
	stage('ContinuousBuild') {
		sh label: '', script: 'mvn package'
	}
	stage('ContinuousDeployment'){
		sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/RaDevPipeline/target/sprintboot-demo.war ubuntu@172.31.27.179:/var/lib/tomcat8/webapps/qaapp.war'
	}
	stage('ContinuousTesting'){
		git 'https://github.com/rajeshr82/FunctionalTesting.git'
		sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/RaDevPipeline/testing.jar'
	}
	stage('ContinuousDeivery'){
		sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/RaDevPipeline/target/sprintboot-demo.war ubuntu@172.31.24.191:/var/lib/tomcat8/webapps/prdapp.war'
	}
}
