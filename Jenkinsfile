pipeline {
    agent any
    environment {
        /*AWS_ACCOUNT_ID="997742452154"
        AWS_DEFAULT_REGION="us-east-2" 
        IMAGE_REPO_NAME="infobelt/isatest"
        REPOSITORY_URI = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}"*/
        BLD_NUMBER = "${env.BUILD_NUMBER}"

    }
    
    stages {
         
         stage('Logging into AWS ECR') {
            steps {
                script {
                //sh "aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"
                sh "echo Hello Jenkins!!"
                //sh "sudo source /home/kudelli/.bashrc"
                sh "whoami"
                }
            }
        }

        stage('Build Release') {          
            steps {
                script {
                    def version = sh script: "/usr/local/apache-maven/bin/mvn help:evaluate -Dexpression=project.version -q -DforceStdout", returnStdout: true
                    sh "echo version value is $version"
                    def pom_toupdate = sh script: "echo ${version} | rev | cut -c2- | rev", returnStdout: true
                    sh "echo pom_toupdate version is $pom_toupdate"
                    def newpomversion = "${pom_toupdate}${BLD_NUMBER}"
                    println(newpomversion)

             }
        }
    }
}
}
