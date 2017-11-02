
pipeline {
   
   docker.withRegistry('https://10.1.53.4/','dtr-login'){
       // dtr-login is a login ID in credentials 
        stage "syncing files"
        git 'https://github.com/knagababu/example-voting-app.git/'

   stages {
      stage('Building and pushing Vote Image') {
        steps {
            echo 'Building..'
			def vote_img = docker.build('dockeradmin/voting-app-vote','./vote').push('latest')
        }
    }
    stage('Building and pushing Worker Image') {
        steps {
            echo 'Testing..'
			def worker_img = docker.build('dockeradmin/voting-app-worker','./worker').push('latest')
        }
    }
    stage('Building and pushing Result Image') {
        steps {
            echo 'Deploying....'
			def result_img = docker.build('dockeradmin/voting-app-result','./result').push('latest')
        }
     }
  }
}
