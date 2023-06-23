
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

