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
                    //sh 'export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-11.0.15.0.9-2.el8_5.x86_64/bin/"'
                    def version = sh script: "mvn help:evaluate -Dexpression=project.version -q -DforceStdout", returnStdout: true
                    sh "echo version value is $version"
                    def pom_toupdate = sh script: "echo ${version} | rev | cut -c2- | rev", returnStdout: true
                    sh "echo pom_toupdate version is $pom_toupdate"
                    //def newpomversion = "${pom_toupdate}${BLD_NUMBER}"
                    //println(newpomversion)
                    //def buildnumber = "$(env.BUILD_NUMBER)"
                    def pom_toupdate_trim = pom_toupdate.trim()
                    def newpomversion = pom_toupdate_trim + '' + BLD_NUMBER
                    println(newpomversion)
                    //println pom_toupdate_trim + BLD_NUMBER

             }
        }
    }
}
}
