pipeline
{
agent any
stages 

{ stage ('scm_checkout')
  { steps { git branch: 'master', url: 'https://github.com/sandipmooreco/maven-project.git' } }


  stage ('execute unit test')
  {steps { withMaven(globalMavenSettingsConfig: 'bdd550d2-4d91-4a69-97d3-877d81cd26ba', jdk: 'local_jdk', maven: 'loal_mvn', mavenSettingsConfig: '26308a25-93b7-4a86-972b-6e63e44e03b3', traceability: true) 
{ sh 'mvn test' } 
 }}


// stage ('run sonar and build the code')
// { steps { withSonarQubeEnv(credentialsId: 'sonar' , installationName: 'sonar') { withMaven(globalMavenSettingsConfig: 'bdd550d2-4d91-4a69-97d3-877d81cd26ba', jdk: 'local_jdk', maven: 'loal_mvn', mavenSettingsConfig: '26308a25-93b7-4a86-972b-6e63e44e03b3', traceability: true) 
//  {  sh 'mvn package sonar:sonar' } 
// } } }


}
}
