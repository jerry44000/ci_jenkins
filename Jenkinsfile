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
        NEXUSIP = '172.31.89.24'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vp-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn -s settingsxml -DskipTests install'
            }
        }
    }
}