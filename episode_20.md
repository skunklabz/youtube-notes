
# Episode 20: Using Azure CLI to Create Azure DevOps Pipelines

## Description
In this quick video I show you how you can create Azure DevOps pipelines using only the Azure CLI. In this demonstration I am using macOS and the Azure CLI in the zsh terminal.

YouTube Video URL: https://youtu.be/jz-1RUNy1Rg

## Steps in video

### Install Azure DevOps Extension

    az extension add --name azure-devops
    
    az devops configure --defaults organization=<URL>
    
    az devops configure --defaults project=<projectName>
    
    az devops -h
    
    az pipelines list --query "[].name"
    
    az repos list --query "[].name"


### CREATE LOCAL PROJECT 

    mkdir testapi
    
    cd testapi
    
    dotnet new webapi -o .
    
    git init .
    
    git add .
    
    git commit -m "Initial commit"

### CREATE REMOTE REPO AND PUSH CODE

    az repos create --name testapi
    
    git remote add origin <sshUrl>
    
    git push origin master

### CREATE PIPELINE

    az pipelines create --name <name>  #NOTE choose 5, then 1
    
    az pipelines build list -o table
    
    az pipelines build list --query "[0].[definition.name, id, result]"

### DELETE PIPELINE

    az pipelines list --query "[].[name,id]"
    
    az pipelines delete --id <id>

