
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
                    for (entries in changeSet) {
                        for (int j = 0; j < entries.length; j++) {
                            def entry = entries[j]
                            def files = new ArrayList(entry.affectedFiles)
                            for (int k = 0; k < files.size(); k++) {
                                def file = files[k]
                                filesList.add(file.path)
                            }
                        }
                    }
                    echo("================")
                }
            }
        }
    }
}

