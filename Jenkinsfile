pipeline{
    agent any
    stages{
        stage('download')
        {
            steps{
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('build')
        {
            steps{
           sh 'mvn package'
            }
        }
        stage('deploy')
        {
            steps{
           deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '45bd33ca-e94a-401e-8690-ea3b444df359', path: '', url: 'http://172.31.17.104:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('test')
        {
            steps{
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline2/testing.jar'
            }
        }
        stage('deliver')
        {
            steps{
           deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '45bd33ca-e94a-401e-8690-ea3b444df359', path: '', url: 'http://172.31.17.206:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
