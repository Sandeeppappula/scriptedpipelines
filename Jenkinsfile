node("built-in")
{

    stage("download")
    {
        
    {
        git 'https://github.com/Sandeeppappula/maven.git'
    }
    }
    stage("build")
    {
        sh 'mvn package'
    }
}
node("myslave")
{
    stage("deploy")
    {
        sh 'scp /var/lib/jenkins/workspace/demo/webapp/target/webapp.war ubuntu@172.31.8.161:/var/lib/tomcat10/test2'
    }
}
    stage("testing")
    {
        git 'https://github.com/Sandeeppappula/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/DemoScriptedPipeline/testing.jar'
    }
    stage("delivery")
    {
        sh 'scp /var/lib/jenkins/workspace/DemoScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.3.43:/var/lib/tomcat10/prod2'
    }
