pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code checkout is handled by Jenkins SCM'
            }
        }

        stage('Show Workspace') {
            steps {
                sh '''
                    echo "Workspace location:"
                    pwd

                    echo "Files pulled from GitHub:"
                    ls -la

                    echo "Latest commit:"
                    git log -1 --oneline
                '''
            }
        }

        stage('Deploy to Nginx') {
            steps {
                sh '''
                    echo "Cleaning nginx web root..."
                    rm -rf /var/www/html/*

                    echo "Copying website files..."
                    cp -r * /var/www/html/

                    echo "Files deployed:"
                    ls -la /var/www/html

                    echo "Pipeline deployment completed."
                '''
            }
        }
    }
}
