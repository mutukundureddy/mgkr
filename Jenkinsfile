pipeline 
{
    agent any
    stages
    {
        stage('continuos download') 
        {
            steps 
            {
             git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continuos build') 
        {
            steps 
            {
             sh 'mvn package'
            }
        }
        stage('continuos deployment') 
        {
            steps 
            {
             deploy adapters: [tomcat9(credentialsId: '76c20b58-9289-4aa8-9da8-93a3133cd15f', path: '', url: 'http://172.31.3.89:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('continuos testing') 
        {
            steps 
            {
             git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
             sh '''java -jar /home/ubuntu/.jenkins/workspace/'declarative pipeline'/testing.jar'''
            }
        }
        stage('continuos delivery') 
        {
            steps 
            {
             deploy adapters: [tomcat9(credentialsId: '76c20b58-9289-4aa8-9da8-93a3133cd15f', path: '', url: 'http://172.31.12.196:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
