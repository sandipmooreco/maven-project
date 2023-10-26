pipeline
{
    agent any
    stages 

    { stage ('scm_checkout')
        { steps { git branch: 'master', url: 'https://github.com/sandipmooreco/maven-project.git' } }


    stage ('execute unit test')
        {steps { withMaven(globalMavenSettingsConfig: 'bdd550d2-4d91-4a69-97d3-877d81cd26ba', jdk: 'local_jdk', maven: 'loal_mvn', mavenSettingsConfig: '26308a25-93b7-4a86-972b-6e63e44e03b3', traceability: true) 
            { sh 'mvn test' } 
                } }       
  
    stage ('deploy package')
        {steps { withMaven(globalMavenSettingsConfig: 'bdd550d2-4d91-4a69-97d3-877d81cd26ba', jdk: 'local_jdk', maven: 'loal_mvn', mavenSettingsConfig: '26308a25-93b7-4a86-972b-6e63e44e03b3', traceability: true) 
            { sh 'mvn clean package' } 
                } }
          
    stage ('maven install')
        {steps { withMaven(globalMavenSettingsConfig: 'bdd550d2-4d91-4a69-97d3-877d81cd26ba', jdk: 'local_jdk', maven: 'loal_mvn', mavenSettingsConfig: '26308a25-93b7-4a86-972b-6e63e44e03b3', traceability: true) 
            { sh 'mvn install' } 
                }}
    stage ('create docker image')
       {steps { sh 'docker build -t 17091332/docker-tomcat-oct23:latest .' }
              }
    stage ('docker push')
      {steps {withDockerRegistry(credentialsId: 'docker_creds', url: 'https://index.docker.io/v1/')
          {
            docker push 17091332/docker-tomcat-oct23:latest
              } } }

}
}
