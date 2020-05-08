pipeline
{
    agent any
    stages
    {
        stage ('scm checkout')
        {
            steps
            {
                git branch: 'master', url: 'https://github.com/kdadhikari/maven-project'
            }
        }
        stage ('compile source code')
        {
            steps
            {
                withMaven(jdk: 'localjdk-8', maven: 'localmvn') 
                {
                    sh 'mvn compile'
                }
            }
        }
        stage ('test')
        {
            steps
            {
                withMaven(jdk: 'localjdk-8', maven: 'localmvn') 
                {
                    sh 'mvn test'
                }

            }
        }
        stage ('package')
        {
            steps
            {
                withMaven(jdk: 'localjdk-8', maven: 'localmvn') 
                {
                    sh 'mvn package'
                }

            }
        }
        stage ('verify')
        {
            steps
            {
                withMaven(jdk: 'localjdk-8', maven: 'localmvn') 
                {
                    sh 'mvn verify'
                }

            }
        }
        stage ('install')
        {
            steps
            {
                withMaven(jdk: 'localjdk-8', maven: 'localmvn') 
                {
                    sh 'mvn install'
                }

            }
        }       
    }
} 
