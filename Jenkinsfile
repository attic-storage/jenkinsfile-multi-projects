modules = [:]
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
    def folders = findFiles(glob: '*')
    for(int i = 0; i < folders.size(); i++) {
        if(folders[i].directory) {
            def directory = folders[i].path
            def modulePath = "${directory}/build.jenkins"
            if(fileExists(modulePath)) {
                def module = load path: modulePath
                modules.put(directory, {
                    dir(directory) {
                        module.build()
                    }
                })
            }
        }
    }
}

def buildModules() {
    parallel modules
}