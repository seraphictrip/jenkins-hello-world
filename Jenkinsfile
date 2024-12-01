pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Echo mvn version') {
            steps {
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean package -DskipTests=true"
                archiveArtifacts 'target/hello-world-*.jar'
            }
        }
        stage('Unit Test') {
            steps {
                sh "mvn test"
                junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
            }
        }
    }
}
