
pipeline {
    agent any
    stages {
        stage('Get ChangeSets') {
            steps {
                script {
                    def author = ""
                    def changeSet = currentBuild.changeSets  
                    def currentBuildId = "$BUILD_ID" as int
                    echo("================")
                    echo "Build Number ${currentBuildId}";
                    echo "ChangeSet Size : ${changeSet.size()}"
                    
                    def changeLogSets = currentBuild.changeSets
                    for (int i = 0; i < changeLogSets.size(); i++) {
                        def entries = changeLogSets[i].items
                        for (int j = 0; j < entries.length; j++) {
                            def entry = entries[j]
                            echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
                            def files = new ArrayList(entry.affectedFiles)
                            for (int k = 0; k < files.size(); k++) {
                                def file = files[k]
                                echo "  ${file.editType.name} ${file.path}"
                            }
                        }
                    }
                    echo("================")
                }
            }
        }
    }
}

