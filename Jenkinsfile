pipeline { 
    agent any 
        stages { 
            stage ('Build') { 
                steps { 
                    echo 'Comincio la fase di build.'
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }
    }
