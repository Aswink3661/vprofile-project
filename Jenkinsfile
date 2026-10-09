pipeline{
    agent any
    tools{
        jdk "JDK17"
        maven "MAVEN3.9"
    }
    environment{
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'Aswink@7801'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.2.222'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }
    stages{
        stage("Build"){
            steps{
                sh"mvn -s settings.xml -DskipTests install"
            }
            post{
                always{
                    echo " Now Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage("Test"){
            steps{
                sh"mvn test"
            }
        }
        stage('check style'){
            steps{
                sh"mvn checkstyle:checkstyle"
            }
        }
    }
}