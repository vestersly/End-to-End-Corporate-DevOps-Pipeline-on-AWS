pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    environment {
        SCANNER_HOME = tool 'Sonar-Scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-creds',
                    url: 'https://github.com/vestersly/End-to-End-Corporate-DevOps-Pipeline-on-AWS.git'
            }
        }

        stage('Compile & Test') {
            steps {
                // We will assume the pom.xml is in the root now
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube-Server') {
                    sh '''
                        $SCANNER_HOME/bin/sonar-scanner \
                        -Dsonar.projectName=VProfile-App \
                        -Dsonar.projectKey=VProfile-App \
                        -Dsonar.sources=. \
                        -Dsonar.java.binaries=**/target
                    '''
                }
            }
        }

        stage('Quality Gate') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }

        stage('Build & Tag Docker Image') {
            steps {
                script {
                    // Make sure the Dockerfile is in the root of your repo
                    def dockerImage = docker.build("vestersly/vprofile-app:${env.BUILD_NUMBER}")
                }
            }
        }

        stage('Scan Docker Image with Trivy') {
            steps {
                // This is still a placeholder
                echo "Trivy scan step is placeholder."
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    // This is now active. It will use the 'dockerhub-creds' we created.
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
                        def image = docker.image("vestersly/vprofile-app:${env.BUILD_NUMBER}")
                        image.push()
                    }
                }
            }
        }
        
        stage('Deploy to Kubernetes') {
            steps {
                // This is still a placeholder
                echo "Deploying to Kubernetes..."
            }
        }
    }
}
