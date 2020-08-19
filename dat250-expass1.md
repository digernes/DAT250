# Software Technology Lab 1: Development Environment and Cloud Deployment

## Installing the software development environment

### JDK

The newest JDK was downloaded from https://www.oracle.com/java/technologies/javase-downloads.html and installed. Added path to the Enviroment Variable. 

**Validation**: Opened the command line and ran ``java -version`` and ``javac -version``. The correct versions were installed. 
 
**Technical difficulties**: Encountered no technical difficulties.

### IDE (VSCode)

After talking with the new group we agreed to use VSCode as IDE for java. I had not used this program for specifically java before, so i installed som expansions for java. 
Everything seemed ok.

### Maven

Downloaded and installed from https://maven.apache.org. Added path to the Enviroment Variable.

**Validation**: Ran ``mvn -version``. The correct version was installed.

**Technical difficulties**: Encountered no technical difficulties.

### Git client

I already had a git client installed.

## Experiment: Heroku and Platform as a Service

I followed the step-by-step "Getting Started" guide. It was an informative, structured and helpful guide to get the gist of Heroku. Cloned the sample app and expirimented a bit with it.

#### Technical difficulties

- When I was trying to set the value of a new config variable, I encountered an error (see below). Something was wrong with the path or the command itself, so I could't set the variable from 
the command line. After some googling and troubleshooting I still didn't find the problem. Instead I manually added the variable ``ENERGY`` from the interface on [the Heroku
website dashboard.](https://dashboard.heroku.com/apps/). 


```
$ heroku config:set ENERGY="12 GeV"
'C:\Program' is not recognized as an internal or external command,
operable program or batch file.
```
