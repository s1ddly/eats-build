pipeline {
    agent any 
    stages {
        stage('Initialise input variables') { 
            steps {
				sh 'echo "Initialising environment"'
				sh 'pwd'
				sh 'ls -l'
            }
        }
		stage('Cloning repo') { 
            steps {
				sh 'echo Cleaning previous repo'
				sh 'rm -rf eats'
				sh 'echo Downloading repo'
                sh 'git clone git@github.com:s1ddly/eats.git'
                sh 'cp list.csv eats/list.csv'
				sh 'cp images/* eats/assets/img/'
				sh 'cd eats; git status; cd python; python3 main.py; cd ..; git status'
				sh 'cd eats; nohup python -m http.server > ../web.log 2>&1 & echo $! > ../web.pid'
				sh 'echo "website is now available to view at http://pi.hole:8000/"'
				input(message:"Deploy code?", ok: "Yes")
				sh 'cd eats; git add .; git commit -m "Updated list.csv - $(date \'+%Y%m%d\')"; git push'
				sh 'kill -9 $(cat web.pid)'
            }
        }
    }
}