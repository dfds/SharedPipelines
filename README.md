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
TODO

#How to use
TODO

#Known issues
Todo

#Getting help
TODO

#Getting involved
TODO