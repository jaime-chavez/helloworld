pipeline {
    agent any
    environment {
        CREDENTIALS_ID ='labkey'  //Google Cloud Storage plugin https://plugins.jenkins.io/google-storage-plugin/
        BUCKET = 'jenkinsbucketlab' 
    }
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!'
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
        stage('Get Last Commit Details') {
            steps {
                script{
                    List<String> changes = getChangedFilesList()
                    println ("Changed file list: " + changes)
                    Integer jenkinsIndex = changes.indexOf("Jenkinsfile")
                    changes.remove(jenkinsIndex)
                    println ("List without jenkisfile: " + changes)
                    changes.each {
                        println "list: ${it}"
                    }
                }
            }
        }
        stage('Store to GCS') {
            steps{
                step([$class: 'ClassicUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}", pattern: "files/*"])
            }
        }
    }
    post {
        always {
            // Uploads build log with name LOG as an object to our GCS bucket.
            step([$class: 'ClassicUploadStep', credentialsId: env.CREDENTIALS_ID,  bucket: "gs://${env.BUCKET}/logs",
                logName: env.LOG])
        }
    }
}

@NonCPS
List<String> getChangedFilesList(){
    def changedFiles = []
    for ( changeLogSet in currentBuild.changeSets){
        for (entry in changeLogSet.getItems()){
            changedFiles.addAll(entry.affectedPaths)
        }
    }
    return changedFiles
}
