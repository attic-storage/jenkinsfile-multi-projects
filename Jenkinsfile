@Library('build-jenkins') _

pipeline {
    agent any
    stages {
        stage('Load modules') {
            steps {
                loadModules()
            }
        }
        stage('Build modules') {
            steps {
                buildModules()
            }
        }
    }
}

def loadModules() {
    modules = loadBuildJenkinsFilesAsModules()
}

def buildModules() {
    parallel modules
}