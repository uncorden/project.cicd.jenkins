pipeline {
    agent any

    environment {
        GIT_CREDENTIALS_ID = 'test_creds'
    }

    stages {
        stage('Checkout Repo') {
            steps {
                git url: 'https://github.com/uncorden/project.cicd.jenkins.git',
                    branch: 'main',
                    credentialsId: "${env.GIT_CREDENTIALS_ID}"
            }
        }

        stage('Show Repo and Branch Info') {
            steps {
                script {
                    // Get the Git remote URL
                    def repoUrl = sh(script: "git config --get remote.origin.url", returnStdout: true).trim()
                    def repoName = repoUrl.tokenize('/').last().replace('.git', '')

                    // Get current branch name
                    def branchName = sh(script: "git rev-parse --abbrev-ref HEAD", returnStdout: true).trim()

                    echo "🔹 Git Repository: ${repoName}"
                    echo "🔹 Branch: ${branchName}"
                }
            }
        }

        stage('Show README.md') {
            steps {
                script {
                    if (fileExists('README.md')) {
                        echo '📄 README.md content:'
                        sh 'cat README.md'
                    } else {
                        echo '⚠️ README.md not found in the repository.'
                    }
                }
            }
        }
    }
}
