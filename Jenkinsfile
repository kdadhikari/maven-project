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
        stage ('tomcat installation')
        {
            steps
            {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /etc/ansible/playbooks/tomcat_instal.yml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//etc//ansible//playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'tomcat_instal.yml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])

            }
        }
    }
} 
