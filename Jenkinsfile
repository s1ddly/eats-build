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
				sh 'cd eats; git status; cd python; sh main.py; cd ..; git status'
            }
        }
    }
}