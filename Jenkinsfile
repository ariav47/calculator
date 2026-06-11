pipeline {
    agent any
    
    tools {
        jdk 'jdk17'
    }

    stages {
        stage ("Compile") {
            steps {
                sh "chmod +x ./gradlew"
                sh "./gradlew compileJava"
            }
        }
        stage ("Unit test") {
            steps {
                sh "./gradlew test"
            }
        }
        // TAHAP BARU:
        stage ("Code coverage") {
            steps {
                sh "./gradlew jacocoTestReport"
                
                // Perintah untuk mempublikasikan laporan HTML
                publishHTML (target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'build/reports/jacoco/test/html',
                    reportFiles: 'index.html',
                    reportName: "JaCoCo Report"
                ])
                
                sh "./gradlew jacocoTestCoverageVerification"
            }
        }
    }
}