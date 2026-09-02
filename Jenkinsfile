node {
  agent {
    label 'LinuxAgentMultiple'
  }  
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for .NET'
    withSonarQubeEnv() {
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"scandotnetcorewithjenkins\" /d:sonar.host.url=\"http://localhost:9002\" /d:sonar.token=\"sqb_4e0471ab2df532ac6a30eb7fb5158dbbc6501ee4\""
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end /d:sonar.token=\"sqb_4e0471ab2df532ac6a30eb7fb5158dbbc6501ee4\""
    }
  }
}
