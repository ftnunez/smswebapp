node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for .NET'
    withSonarQubeEnv() {
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"smsSonar\" /d:sonar.host.url=\"http://localhost:9000\" /d:sonar.token="\sqp_141d22a718a4c3320b329ca7ed85ddb08cfd2fac\""
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end /d:sonar.token=\"sqp_141d22a718a4c3320b329ca7ed85ddb08cfd2fac\""
    }
  }
}
