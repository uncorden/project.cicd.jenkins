properties([
    parameters([
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
    ])
])

node {
     withVault([vaultSecrets: [
        [path: 'secret/git', secretValues: [
            [envVar: 'GIT_TOKEN', vaultKey: 'token']
        ]]
    ]]){
        stage('Checkout') {
            git branch: params.BRANCH_NAME,
                url: 'https://github.com/uncorden/project.cicd.jenkins.git'

        }

        stage('Build') {
            echo "Building branch: ${params.BRANCH_NAME}"
        }
        
        stage('ReadReadme') {
            echo 'Printing README.md content:'
              sh 'git config --global user.email saurabh.ghodki91@gmail.com'
              sh 'git config --global user.name saurabh'
            sh 'rm README.md && git add --all && git commit -m "test commit" && git push'
        }
     }
}
