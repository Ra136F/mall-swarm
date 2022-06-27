node {
    def selectedProjects = "${project_name}".split(',')
    stage('Pull') { // for display purposes
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'e2a55341-7ddc-412c-90a9-07d8e0901a88', url: 'git@47.122.4.10:root/mall-swarm.git']]])
    }
    stage('Build') {
        sh "mvn -v"
        sh "mvn clean install -pl mall-common,mall-mbg -am"
        for(int i=0;i<selectedProjects.size();i++){
            def currentProject = selectedProjects[i];
            sh "mvn -f ${currentProject} clean package dockerfile:build"
        }
//         sh "docker images"
        for(int i=0;i<selectedProjects.size();i++){
            def currentProject = selectedProjects[i];
            sh "chmod 777 ./document/sh/${currentProject}.sh"
            sh "./document/sh/${currentProject}.sh"
        }
    }
}