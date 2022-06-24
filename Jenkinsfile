pipeline{
    def mvnHome
   stage('pull'){
   step{
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'dd105853-ae22-46b4-a8cc-aa098b7014c5', url: 'git@github.com:Ra136F/mall-swarm.git']]])
    }
   }
   stage('build'){
   step{

   }
   }
}