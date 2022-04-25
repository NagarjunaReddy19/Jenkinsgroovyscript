node
 {
  def mavenHome = tool name: "maven 3.8.5"
  stage('codechechout')
  {
   git branch: 'development', credentialsId: '75e317df-fb47-4244-954b-f04793be1036', url: 'https://github.com/NagarjunaReddy19/maven-web-application.git'
  }
  stage('build')
  {
  sh "${mavenHome}/bin/mvn clean package"
  }
  stage('uploadtonexus')
   {
  sh "${mavenHome}/bin/mvn deploy"
  }
   stage('tomcat')
  {
   sshagent(['4959ca1b-6d2f-4016-8f58-ed9fc1eeeb6a']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.127.8.25://opt/apache-tomcat-9.0.62/webapps"
   }
  }
  stage('email')
  {
    emailext body: 'hi', subject: 'mm', to: 'dnagarjunareddy007@gmail.com'
  }
 }
