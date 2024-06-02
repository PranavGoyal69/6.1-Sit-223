pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                bat 'git --version' // Ensure Git is available
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    try {
                        // Example build command for Windows
                        bat 'echo Building the project'
                        bat 'echo Build successful' // Simulate build success
                    } catch (Exception e) {
                        echo "Build failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Build failed")
                    }
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    try {
                        // Simulate running tests
                        bat 'echo Running unit and integration tests'
                    } catch (Exception e) {
                        echo "Tests failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Tests failed")
                    }
                }
            }
        }
        
        stage('Code Analysis') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    try {
                        // Simulate code analysis
                        bat 'echo Running code analysis'
                    } catch (Exception e) {
                        echo "Code analysis failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Code analysis failed")
                    }
                }
            }
        }
        
        stage('Security Scan') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    try {
                        // Simulate security scan
                        bat 'echo Running security scan'
                    } catch (Exception e) {
                        echo "Security scan failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Security scan failed")
                    }
                }
            }
        }
        
        stage('Deploy to Staging') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    try {
                        // Simulate deployment to staging
                        bat 'echo Deploying to staging'
                    } catch (Exception e) {
                        echo "Staging deployment failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Staging deployment failed")
                    }
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    try {
                        // Simulate integration tests on staging
                        bat 'echo Running integration tests on staging'
                    } catch (Exception e) {
                        echo "Integration tests on staging failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Integration tests on staging failed")
                    }
                }
            }
        }
        
        stage('Deploy to Production') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                script {
                    try {
                        // Simulate deployment to production
                        bat 'echo Deploying to production'
                    } catch (Exception e) {
                        echo "Production deployment failed: ${e.getMessage()}"
                        currentBuild.result = 'FAILURE'
                        error("Production deployment failed")
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                // Collect and archive logs
                archiveArtifacts artifacts: '**/*.log', allowEmptyArchive: true
            }
        }
        success {
            emailext(
                subject: 'Build Successful',
                body: '''<p>Build completed successfully.</p>
                         <p>See attached logs for more details.</p>''',
                to: 'gpranav2901@gmail.com',
                attachLog: true
            )
        }
        failure {
            emailext(
                subject: 'Build Failed',
                body: '''<p>Build failed. Please check the logs.</p>
                         <p>See attached logs for more details.</p>''',
                to: 'gpranav2901@gmail.com',
                attachLog: true
            )
        }
    }
}
