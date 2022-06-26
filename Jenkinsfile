node {
    def selectedProjects = "${project_name}".split(',')
    stage('Pull') { // for display purposes
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '1840d0fc-c097-47af-8730-7cc9415ebe9f', url: 'git@github.com:Ra136F/mall-swarm.git']]])
    }
    stage('Build') {
        sh "mvn -v"
        sh "mvn clean install -pl mall-common,mall-mbg -am"
        for(int i=0;i<selectedProjects.size();i++){
            def currentProject = selectedProjects[i];
            sh "mvn -f ${currentProject} clean package"
        }
//         sh "docker images"
        for(int i=0;i<selectedProjects.size();i++){
            def currentProject = selectedProjects[i];
            sh "chmod 777 ./document/sh/${currentProject}.sh"
            sh "./document/sh/${currentProject}.sh"
        }
    }
}