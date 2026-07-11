node('built-in') 
{
    stage('ContinuousDownlod') 
    {
        git 'https://github.com/IntelliqDevops/maven.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('Deployment') 
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '36ae92a4-5d2c-4e85-af95-1d9479531187', path: '', url: 'http://172.31.8.161:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '36ae92a4-5d2c-4e85-af95-1d9479531187', path: '', url: 'http://172.31.3.43:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
