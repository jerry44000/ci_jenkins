pipeline {
    agent any
    tools {
        maven "maven3"
        jdk "OracleJDK8"
    }

    environment {
        SNAP_REPO = 'vp-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'azerty'
        RELEASE_REPO = 'vp-release'
        CENTRAL_REPO = 'vp-maven-central'
        NEXUSIP = '172.31.84.70'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vp-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        post {
            success {
                echo "Now Archiving."
                archiveArtifacts artifacts: '**/*.war'
            }
        }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Checkstyle Analysis') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
    }
}