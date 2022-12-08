// basic FOSSA integration

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git credentialsId: 'MyGitHub', url: 'https://github.com/justinTsugranes/Dropiwizard-Template'
                sh './gradlew spotlessApply clean build'
            }
        }
        stage('Analyze'){
            steps {
                echo 'Analyzing...'
                    sh 'curl -H \'Cache-Control: no-cache\' https://raw.githubusercontent.com/fossas/fossa-cli/master/install-latest.sh | bash'
                  
          }
        }
        stage('Run FOSSA') {
            steps {
                echo 'Running FOSSA...'
                sh 'FOSSA_API_KEY=a3acf20770ac9b9e0cf93d302ca15fc6 /usr/local/bin/fossa analyze'
            }
        }
        // cannot use PUSH ONLY API KEY HERE - DO NOT EXPOSE A NON-PUSH ONLY TOKEN
        // stage('Run FOSSA test') {
        //     steps {
        //         echo "Running FOSSA test..."
        //         sh "FOSSA_API_KEY=XXXXXXXXXX /usr/local/bin/fossa test"
        //     }
        // }
        stage('Test') {
              steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
              steps {
                echo 'Deploying....'
            }
        }
    }
}