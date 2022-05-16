node {
    stage('Prepare') {
        properties([pipelineTriggers([githubPush()])])
        checkout scm
        sh 'maven clean'
    }

    stage('Build') {
        sh 'maven compile'
        sh 'maven hpi:hpi'
    }

    stage('Archive') {
        archiveArtifacts 'target/discord-notifier.hpi'
    }
}
