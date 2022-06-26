node {
    def selectedProjects = "${project_name}".split(',')
    stage('Pull') { // for display purposes
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '0fc6b6eb-d995-4644-890d-8513bfc3031b', url: 'git@github.com:Ra136F/mall-swarm.git']]])
    }
    stage('Build') {

        sh "printenv"
        sh "mvn -v"
        sh "mvn clean install -pl mall-common,mall-mbg -am"

        for(int i=0;i<selectedProjects.size();i++){
            def currentProject = selectedProjects[i];
            sh "mvn -f ${currentProject} clean package"
        }
        for(int i=0;i<selectedProjects.size();i++){
            def currentProject = selectedProjects[i];
            sh "./document/sh/${currentProject}.sh"
        }
    }
}