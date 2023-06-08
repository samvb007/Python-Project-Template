pipeline { 

    agent any 

     stages { 

        stage('Checkout') { 

            steps { 

                // Checkout your source code from the repository 

                // Replace the repository URL and credentials as needed 

                git 'https://github.com/samvb007/Python-Project-Template.git' 

            } 

        } 
         
        stage('Remove Existing File') { 

            steps{ 

                sh 'rm result.xml' 

                sh 'rm coverage.xml' 

            } 

        } 

        stage('Build') { 

            steps { 

                // Checkout your source code from the repository 

                // Replace the repository URL and credentials as needed 

               // sh 'pip install -r requirements-dev.txt' 

               // sh 'pip install pytest'  

                sh 'python3 -m pytest tests --junitxml=result.xml'  

                sh 'python3 -m pytest  --cov-report=xml --cov=tests'  

            } 

        } 

        stage('SonarQube Analysis') { 

            steps { 

                script{ 

                    def scannerHome = tool 'sonar-scanner'; 

                    withSonarQubeEnv(installationName:'sonar-server',credentialsId: 'FirstProject-token') { 

                        echo 'Process Start For Sonarqube' 

                        sh ''' ${scannerHome}  

                                    -Dsonar.projectKey=FirstProject  '''

//                                     -Dsonar.host.url=http://172.18.0.3:9000  

//                                     -Dsonar.token=sqp_e6b90d8c1f911c7c6bf9c1d4bb0954aa960c22eb  

//                                     -Dsonar.projectVersion=1.0 

//                                     -Dsonar.sources=. 

//                                     -Dsonar.language=py  

//                                     -Dsonar.sourceEncoding=UTF-8  

//                                     -Dsonar.inculsions=sample.xml  

//                                     -Dsonar.python.xunit.reportPath=result.xml  

//                                     -Dsonar.python.coverage.reportPaths=coverage.xml ''' 

                    } 

               } 

            } 

        } 

     } 

    post('Publish') { 

        always{ 

            xunit checksName: "", tools: [JUnit(excludesPattern: "", pattern: "result.xml", stopProcessingIfError: true)]  

            publishCoverage adapters: [sonarGenericCoverageAdapter("coverage.xml")]  

        } 

    } 

} 
