node('master'){
stage 'checkout'
git branch: 'master', credentialsId: '1bc9767b-c85b-4ba1-b03e-9c42ca5a22f5', url: 'https://github.com/pradeep-99/JAVA_Project.git'
def isMaster = env.BRANCH_NAME == 'master'
def isDevelop = env.BRANCH_NAME == 'develop'
String jobInfo = "${env.JOB_NAME} ${env.BUILD_DISPLAY_NAME} \n${env.BUILD_URL}"
currentBuild.result = "SUCCESS"
//Assigning parameters
 //   parameters: [
 //   string(name: 'EAR_TAG', value: EAR_TAG),
 //   string(name: 'VERSION_TAG', value: VERSION_TAG),
 //   string(name: 'SNAPSHOT', value: SNAPSHOT)
 //   ]
// calling the job
    //build job: 'DEV-JOB',
//this
//Code checkout stage
stage 'checkout'
def workspace = pwd()
echo "\u2600 workspace=${workspace}"
// Get code from repository
//git branch: 'dev_branch', credentialsId: '1bc9767b-c85b-4ba1-b03e-9c42ca5a22f5', url: 'https://github.com/pradeep-99/aravind_maven.git'
//stash name: "config", includes: "*"
sh 'ls -ltr ${workspace}'
echo "JAVA_HOME is ${env.JAVA_HOME} on this machine"
//get the maven tool
// This M3 aven tool must configured global configuration in jenkins	
def MAVEN_HOME = B:\build&release_new_softwares\apache-maven-3.2.5 'M3'
withEnv(["PATH+MAVEN_HOME=${tool 'm3'}/bin"]) {
    sh "${MAVEN_HOME}/bin/mvn clean package"
}
//Mark the code build stage
stage 'Build'
//Run the maven build
sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
//string parameters
build job: 'DMA'
parameters: [string(name: 'Insight', value: Insight), string(name: 'LoadType', value: LoadType), string(name: 'Date_As_Of', value: Date_As_Of)]
stage 'deploy'
sh './mydeployment.sh'
//Archieving artifacts
archiveArtifacts artifacts: '/**/**/target/', onlyIfSuccessful: true
//code sonar conditions
codesonar(conditions: [])
//change current directory
dir {
    // some block
}
//Email extention send to devops team
mail to: 'devops@acme.com',
    subject: "Job '${JOB_NAME}' (${BUILD_NUMBER}) is waiting for input",
    body: "Please go to ${BUILD_URL} and verify the build"
//ENV Environment variables are accessible from Groovy code as env.VARNAME or simply as VARNAME. You can write to such properties as well (only using the //env. prefix):

env.MYTOOL_VERSION = '1.33'
node {
    sh '/usr/local/mytool-$MYTOOL_VERSION/bin/start'
}
}
​
