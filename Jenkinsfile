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
                sh "./gradlew jacocoTestCoverageVerification"
            }
        }
    }
}