node
{
    docker.withRegistry('https://10.1.53.4/','dtr-login')
	{
       // dtr-login is a login ID in credentials 

	stages 
		{
			stage('syncing files') 
		{
            steps 
			{
                git 'https://github.com/sysgain/example-voting-app.git'
            }
        }
		
			stage('Building and pushing Vote Image') 
		{
            steps 
			{
                def vote_img = docker.build('dockeradmin/voting-app-vote','./vote').push('latest')
            }
        }
		
		stage('Building and pushing Worker Image') 
		{
            steps 
			{
                def worker_img = docker.build('dockeradmin/voting-app-worker','./worker').push('latest')
            }
        }
		
		stage('Building and pushing Result Image') 
		{
            steps 
			{
                def result_img = docker.build('dockeradmin/voting-app-result','./result').push('latest')
            }
        }
		
		}
   }
}
