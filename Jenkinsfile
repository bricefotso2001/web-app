node('master')
  {
   def mavenHome = tool name: 'maven3.8.5'
  stage('1.git clone')
  {
  git credentialsId: 'bricefotso2001/****** (github_credentials)', url: 'https://github.com/bricefotso2001/web-app.git'
  }
  stage('2mavenBuild')
  { 
    sh "${mavenHome}/bin/mvn clean package"
  }
  stage('3CodeQualityReport')
  {
    sh "${mavenHome}/bin/mvn sonar:sonar"
  }
  stage('4.DeployUATTomcat')
        {
deploy adapters: [tomcat8(credentialsId: 'tomcat8', path: '', url: 'http://18.188.175.198:8080/')], contextPath: null, war: 'target/*.war'
  }
  }
