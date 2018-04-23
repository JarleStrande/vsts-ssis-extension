![Build Status](https://toxicglobe.visualstudio.com/_apis/public/build/definitions/62790b7f-50dd-4a0e-8954-b613d4a9e98b/44/badge) 

Current Version: 1.0.1142

# Introduction
VSTS Extension task to build and deploy Visual Studio Project - SQL Server Integration Services using the Project Deployment Model

## Quick links
- [Task Requirements](#task-requirements)
- [How to setup Build Task](#how-to-setup-build-task)
- [How to setup Deploy Task](#how-to-setup-deploy-task)
- [Latest Updates](#latest-updates)

## Tasks Description
##### Build Task
Build Visual Studio project, containing packages and parameters. It is built to a project deployment package (.ispac)
https://msdn.microsoft.com/en-us/library/hh213290.aspx

##### Deploy Task
Deploy .ispac package to SSIS instance using windows authentification (SQL auth is not possible by MSSQL security architecture)

## Task Requirements
##### Build Task
SQL Server Data tools must be installed on the Agent Server (Build Server)
Download: https://docs.microsoft.com/en-us/sql/ssdt/download-sql-server-data-tools-ssdt

_SSDT for VS2017 can be installed on the Agent Server (Build Server) in New Instance or as part of Visual Studio.
Please select the correct [Instance Option](#devenv-instance-options)_

##### Deploy Task
SQL Shared Management Objects must be installed on the Agent Server (Release Server)
Download: https://www.microsoft.com/en-us/download/confirmation.aspx?id=54279

_Please make sure Agent Service account have appropriate permission on the target SQL Server_

### How to setup Build Task
![image](/images/build.png)

### How to setup Deploy Task
![image](/images/deploy.png)

##### Project Parameters
Parameter must be set in Project. Task will replace values only. Inline or File options.

Inline JSON Example:
```
{
   "parameters":[
      {
	     "Name":  "TestParameter1",
	     "Value": "TestParameterValue1"
      },
      {
	     "Name":  "TestParameter2",
	     "Value": "TestParameterValue2"
      }
   ]
}
```

##### Devenv Instance Options
See [Build Task Requirements](#build)

| SSDT Version / VS Version  |
|:--------------------|
| VS2013 All Versions |
| VS2015 All Versions |
| VS2017 Enterprise   |
| VS2017 Professional |
| VS2017 Community    |
| VS2017 New Instance | 
| Hosted VS2017       |
| Custom 		      |

## Contribution
[file an issue](https://github.com/ToxicGlobe/VSTS-SSIS-Extension/issues) for bug fixes and features and discuss existing proposals

## Latest Updates

1.0.0
> Supported version TFS 2017 and later, VSTS - Hosted Agent, Hosted Agent 2017

> Implemented option for Custom path to Devenv

0.3.4
> Supported version TFS 2013, 2015, 2017, VSTS Hosted Agent
