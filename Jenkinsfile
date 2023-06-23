
pipeline {
    agent any
    stages {
        stage('Get ChangeSets') {
            steps {
                script {
                    def author = ""
                    def changeSet = currentBuild.changeSets  
                    echo("================")
                    echo "ChangeSet Size : ${changeSet.size()}"
                    for (i in changeSet) {
                        echo i
                    }
                    echo("================")
                }
            }
        }
    }
}

