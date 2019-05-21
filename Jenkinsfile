node('agent') {
  stage('SCM') {
    checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: 'refs/heads/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/uladzimiramelyanovich/hello.git']]]
  }
  stage ('Groovy samples') {
	x = 1
	println x
  }
  stage('SonarQube Analysis') {

  sh "/home/jenkins/workspace/tools/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner -X -Dsonar.host.url=http://172.30.0.10:9000 -Dsonar.scm.provider=git -Dsonar.projectName=hello -Dsonar.projectVersion=1.0 -Dsonar.projectKey=hello:app -Dsonar.sources=. -Dsonar.projectBaseDir=/home/jenkins/workspace/"
    }
  }
  stage('Build') {
    sh 'cd /hello'
	sh 'cmake .'
  }
  stage('Test') {
    println 'Test will be here'
  }  
  stage('Deploy') {
    sh "make hello"
  }    