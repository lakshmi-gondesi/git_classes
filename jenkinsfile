node('built-in') {
    
    stage('download') {
   git 'https://github.com/IntelliqDevops/maven.git'
}
    
    stage('build') {
    sh 'mvn package'
}

    stage('deploy') {
    deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '02db91c7-3038-4b72-ade8-7fd682fba596', path: '', url: 'http://172.31.1.136:8080')], contextPath: 'testapp', war: '**/*.war'
}
   stage('test') {
    git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
}
   stage('deliver'){
       sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
   }
   }

