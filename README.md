# Introduction 
Please note security pipelines in this repo is currenlty in Alpha and should not be used in production

#Bronze security package
The bronze security package is used for passive scanning only, this package is the first steps to getting observability on how secure your system is.

#Silver security package
The silver security package is used to start to block critial vulnerabilities for entering your applications, it will also block any infrasture of code misconfigurations if found.

#Gold security package
The Gold security package is used to start to block all of silver including high vulnerabilities from entering your applications.

#Platinum security package
The Platinum security package is used to start to block all of Gold including Medium vulnerabilities from entering your applications.


#Marking false positives
TODO

##Trivy

For instance, if after reading about a particular issue and deciding I can safely ignore it, I add the following line into .trivyignore:
```yml
    # a libc vulnerability in the base image, currently unfixed
    CVE-2021-33574
```

#Project requirements
TODO

#Scanners used
DAST         - OWASP Zap
SCA          - OWASP Dependancy Check
SAST         - Semgrep
IAC          - TF-Sec
Secrets Scan - GitLeaks

#How to use

```yml
    
pool:
  vmImage: 'ubuntu-latest'
  
resources:
  repositories:
    - repository: SharedPipelines
      type: git
      name: CloudEngineering/SharedPipelines

stages:
- stage: Scan
  jobs:
  - job:
    steps:
    - template: 'security-pipeline-packages/gold-security.yml@SharedPipelines'
      parameters:
        sourceDirectory: $(Build.SourcesDirectory) #Source directory containing your code [optional this will detail to $(Build.SourcesDirectory)]
        fullImageUri: <aws_account>.dkr.ecr.<region>.amazonaws.com/<imageName>:<tag> #Full image url [optional for container scan]
        containerPort: 8080 #Container Port [optional for container scan]
        targetPort: 8080 #Container target [optional for container scan]
        containerEnviromentVariables: $(containerEnvVars) #Container Enviroment Variables [optional for container scan]
```

#Known issues
None at the moment

#Getting help
Contact Cloud Engineering.

#Getting involved
Please feel free to add a issue or raise a pull request.