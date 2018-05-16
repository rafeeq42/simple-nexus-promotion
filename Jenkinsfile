pipeline {
    agent none
    stages {
        stage('Retrieve') {
            agent any
            steps {
                sh 'wget http://nexus.roundtower.io:8081/repository/rtt-snapshot/apps/add2vals/1.0/add2vals-1.0'
                sh 'mv add2vals-1.0 /tmp/add2vals'
            }
        }
        stage("Publish") {
           agent any
           steps {
               nexusArtifactUploader(
                   nexusVersion: 'nexus3',
                   protocol: 'http',
                   nexusUrl: 'nexus.roundtower.io:8081',
                   groupId: 'apps',
                   version: '1.0',
                   repository: 'training6-release',
                   credentialsId: 'NexusDefault',
                   artifacts: [
                       [artifactId: 'add2vals',
                        classifier: '',
                        file: '/tmp/add2vals',
                        type: '']
                   ]
               )
           }
        }
    }
}
