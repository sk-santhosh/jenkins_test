// Required due to JENKINS-27421
@NonCPS
List<List<?>> mapToList(Map map) {
  return map.collect { it ->
    [it.key, it.value]
  }
}

pipeline {
    agent any
    stages {
        stage('Get ChangeSets') {
            steps {
                script {
                    def author = ""
                    def currentBuildId = "$BUILD_ID" as int
                    echo("================")
                    echo "Build Number ${currentBuildId}";
                    def changeLogSets = currentBuild.changeSets
                    echo "ChangeSet Size : ${changeLogSets.size()}"
                    for (int i = 0; i < changeLogSets.size(); i++) {
                        def entries = changeLogSets[i].items
                        for (entry in entries) {
                            echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"

                            for (kv in mapToList(entry)){
                                echo "${kv[0]} ${kv[1]}"
                            }
                        }
                    }
                    echo("================")
                }
            }
        }
    }
}

