node('built-in') 
{
    stage('continuous download')
    {
    git 'https://github.com/mutukundureddy/mgkr.git'
    }
    stage('continuous build')
    {
    sh 'mvn package'
    }
    stage('continuous deployment')
    {
    deploy adapters: [tomcat9(credentialsId: '76c20b58-9289-4aa8-9da8-93a3133cd15f', path: '', url: 'http://172.31.3.89:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuous testing')
    {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('continuous delivery')
    {
      input message: 'approved for dm', submitter: 'hari'  
    deploy adapters: [tomcat9(credentialsId: '76c20b58-9289-4aa8-9da8-93a3133cd15f', path: '', url: 'http://172.31.12.196:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
