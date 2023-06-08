pipeline{
    agent any
    //Specify what tool you want to use
    //The tool name needs to match the one you used in your jenkins conf
    tools {
        terraform 'Terraform'
    }
     stages{
         //Check the version and download any changes 
        stage('Git Checkout'){
            steps{
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Nevralgie/TerraxJenkins']])
            }
        }
        //Initiate the directory as the current workspace
        stage('Terraform init'){
            steps{
                sh 'terraform init'
            }
        }
        //Plan your deployment
        stage('Terraform plan'){
            steps{
                sh 'terraform plan'
            }
        }
        //Apply your deployment
        //Note that if the -auto-approve flag is not present, jenkins can not approve the apply and the build will fail.
        stage('Terraform apply'){
            steps{
                sh 'terraform apply -auto-approve'
            }
    }
}
}
