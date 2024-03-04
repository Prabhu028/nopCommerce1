pipeline{
    agent any
    stages{
        stage('VCS'){
            steps{
             git branch: 'develop', url: 'https://github.com/Prabhu028/nopCommerce1.git'
            }
          }
        stage('.NET_build'){
            steps{
                sh'dotnet restore src/NopCommerce.sln'
                sh'dotnet build -c Release src/NopCommerce.sln'
                sh'dotnet publish -c Release src/Presentation/Nop.Web/Nop.Web.csproj -o publish'
                sh'mkdir -p publish/bin publish/logs'
                sh'zip -r nopCommerce.zip publish'
                archive '**/nopCommerce.zip'
            }
        }  
    }
    
}
