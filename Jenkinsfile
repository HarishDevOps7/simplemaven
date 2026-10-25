pipeline {
    agent any

    stages {
        stage('Maven WAR Build') {
            steps {
                sh '/opt/maven/bin/mvn clean package'
            }
        }

        stage('SonarQube Code Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        /opt/maven/bin/mvn \
                        org.sonarsource.scanner.maven:sonar-maven-plugin:sonar \
                        -Dsonar.projectKey=my-war-project
                    '''
                }
            }
        }
    }
}
