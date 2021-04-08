pipeline{

    agent any
    
    options {
        sidebarLinks([
            [displayName: 'Google', iconFileName: 'userContent/Google.jpg', urlName: 'https://google.com/']
        ])
    }

    stages {
        
        stage ('Compile Stage') {

            steps {

                withMaven(maven: 'maven_3_6_3') {
                    sh 'mvn clean install'

                }

            }
        }
    stage ('Test Stage') {

            steps {

                withMaven(maven: 'maven_3_6_3') {
                    sh 'mvn test'

                }

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }

    }

}
