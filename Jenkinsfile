
pipeline {
    agent any
    stages {
        stage('Get ChangeSets') {
            steps {
                script {
                    def changes = ""
                    def currentBuildId = "$BUILD_ID" as int
                    echo("================")
                    echo "Build Number ${currentBuildId}";
                    def changeLogSets = currentBuild.changeSets
                    echo "ChangeSet Size : ${changeLogSets.size()}"
                    for (int i = 0; i < changeLogSets.size(); i++) {
                        def entries = changeLogSets[i].items
                        for (entry in entries) {
                            changes += "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg} \n"
                        }
                    }
                    echo("${changes}================")
                }
            }
        }
    }
}

