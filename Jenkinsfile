node {
    def selectedProjects = "${project_name}".split(',')
    stage('Pull') { // for display purposes
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '34253aae-332d-4bc7-bcba-6bb5b4d56c62', url: 'git@github.com:Ra136F/mall-swarm.git']]])
    }
    stage('Build') {
        sh "mvn -v"
//         sh "mvn clean install -pl mall-common,mall-mbg -am"
//         for(int i=0;i<selectedProjects.size();i++){
//             def currentProject = selectedProjects[i];
//             sh "mvn -f ${currentProject} clean package"
//         }
        sh "./document/sh/mall-admin.sh"
//         for(int i=0;i<selectedProjects.size();i++){
//             def currentProject = selectedProjects[i];
//             sh "./document/sh/${currentProject}.sh"
//         }
    }
}