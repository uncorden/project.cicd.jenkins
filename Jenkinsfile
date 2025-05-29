properties([
    parameters([
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
    ])
])

node {
    stage('Checkout') {
        git branch: params.BRANCH_NAME,
            url: 'https://github.com/uncorden/project.cicd.jenkins.git',
            credentialsId: 'test_creds'
    }

    stage('Build') {
        echo "Building branch: ${params.BRANCH_NAME}"
    }
}
