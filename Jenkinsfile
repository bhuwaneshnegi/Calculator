pipeline {
    agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3911"
    }

    stages {
          stage('Build') {
            steps {
                // Get some code from a GitHub repository
               // git 'https://github.com/jglick/simple-maven-project-with-tests.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.skip=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            //post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
               // success {
                //    junit '**/target/surefire-reports/TEST-*.xml'
                  //  archiveArtifacts 'target/*.jar'
                //}
            }
        //stage('test'){
          //  steps{
            //    sh 'mvn test'
            //}
        //}
        stage('Deploy'){
            steps{
                sh 'scp /var/lib/jenkins/workspace/Demo-calci/target/*.jar ec2-user@13.232.211.5:/home/ec2-user/apache-tomcat-9.0.111/webapps'
            }
        }
    }
}
