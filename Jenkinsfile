pipeline {
    agent any

    environment {
        PROJECT_NAME = "Securite-JuiceShop"
    }

    stages {
        // 1. Checkout
        stage('Checkout') {
            steps {
                echo "1. Recuperation du code source..."
                checkout scm
            }
        }

        // 2. Build / Preparation
        stage('Build / Preparation') {
            steps {
                echo "2. Preparation de l environnement..."
                bat 'npm install --package-lock-only'
            }
        }

        // 3. Security Analysis (SCA)
        stage('Security Analysis') {
            steps {
                echo "3. Analyse des vulnerabilites des dependances (npm audit)..."
                bat 'npm audit --json > reports/npm-audit-report.json || exit 0'
            }
        }

        // 4. Additional Security Check (Detection de secrets)
        stage('Additional Security Check') {
            steps {
                echo "4. Verification additionnelle (Secrets)..."
                bat 'npx gitleaks detect --source . --report-path reports/gitleaks-report.json --no-git || exit 0'
            }
        }

        // 5. Report Generation
        stage('Report Generation') {
            steps {
                echo "5. Archivage des rapports d audit..."
                archiveArtifacts artifacts: 'reports/*.json', allowEmptyArchive: true
            }
        }

        // 6. Notification
        stage('Notification') {
            steps {
                echo "6. Notification : Controles de securite termines."
            }
        }
    }

    post {
        always {
            echo "Execution terminee. Consultez le dossier reports/."
        }
    }
}
