pipeline { 
    agent any 
        stages { 
            stage ('Build') { 
                steps { 
                    echo 'Comincio la fase di build.'
                    sh 'mvn -B -DskipTests clean package'
                }
            }
            stage('Test') {
                steps {
                    echo 'Effettuo il test del codice appena buildato'
                    sh 'mvn test'
                }
                post {
                    always {
                        echo 'Eseguo il plugin jeunit, come consigliao, che produce log xml'
                        junit 'target/surefire-reports/*.xml'
                        archiveArtifacts 'target/*.jar'
                    }
                }
            }
            stage('Deliver') {
                steps {
                    sh './jenkins/scripts/deliver.sh'
                }
            }
        }
}
