#Shared Pipelines
Repository for shared Pipelines.

##Security Packages

### Introduction 
Please note security pipelines in this repo is currenlty in Alpha and should not be used in production

###Current Version 
Version : v1.0.0

###Bronze security package
The bronze security package is used for passive scanning only, this package is the first steps to getting observability on how secure your system is.

###Silver security package
The silver security package is used to start to block critial vulnerabilities for entering your applications, it will also block any infrasture of code misconfigurations if found.

###Gold security package
The Gold security package is used to start to block all of silver including high vulnerabilities from entering your applications.

###Platinum security package
The Platinum security package is used to start to block all of Gold including Medium vulnerabilities from entering your applications.

###Marking false positives
- SamGrep - [https://semgrep.dev/docs/ignoring-files-folders-code/#reference-summary](https://semgrep.dev/docs/ignoring-files-folders-code/#reference-summary)
- Tfsec - [https://aquasecurity.github.io/tfsec/v0.61.3/getting-started/configuration/ignores/](https://aquasecurity.github.io/tfsec/v0.61.3/getting-started/configuration/ignores/)
- Trivy - [https://aquasecurity.github.io/trivy/v0.19.1/vulnerability/examples/filter/](https://aquasecurity.github.io/trivy/v0.19.1/vulnerability/examples/filter/)
- Dependency Check - [https://jeremylong.github.io/DependencyCheck/general/suppression.html](https://jeremylong.github.io/DependencyCheck/general/suppression.html)

###Project requirements
- SamGrep Supported Language - [https://semgrep.dev/docs/language-support/](https://semgrep.dev/docs/language-support/)
- tfsec - Terraform
- SCA Supported Language - [https://jeremylong.github.io/DependencyCheck/analyzers/index.html](https://jeremylong.github.io/DependencyCheck/analyzers/index.html)
- Trivy - [https://aquasecurity.github.io/trivy/v0.20.1/vulnerability/detection/language/](https://aquasecurity.github.io/trivy/v0.20.1/vulnerability/detection/language/)
- Dependancy Check - [https://jeremylong.github.io/DependencyCheck/analyzers/index.html](https://jeremylong.github.io/DependencyCheck/analyzers/index.html)

###Scanners used
- DAST             - OWASP Zap
- SCA              - Dependancy Check
- SAST             - Semgrep
- IAC              - Tfsec
- Secrets Scan     - GitLeaks
- Docker File Scan - Trivy

###How to use

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

###Known issues
None at the moment

##Getting help
Contact Cloud Engineering.

##Getting involved
Please feel free to add a issue or raise a pull request.