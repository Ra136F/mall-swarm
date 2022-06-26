node {
    def selectedProjects = "${project_name}".split(',')
    stage('Pull') { // for display purposes
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '0fc6b6eb-d995-4644-890d-8513bfc3031b', url: 'git@github.com:Ra136F/mall-swarm.git']]])
    }
    stage('Build') {
        sh "export M2_HOME=/home/feng/apache-maven-3.8.6"
        sh "export PATH=$M2_HOME/bin"
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