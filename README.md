# Hello World PVA Ephemral Deployment

## Description
The following example demonstrates a job that creates an ephemeral Docker container in Azure and upload/deploys/replaces a pva on the server and runs a hetakthcheck step against it to validate it.

## User Flow

1.	User checks assets into SCM. Typically this is done via git commit/push/etc or EGit plugin for Eclipse. The user may check in any or all of the following:
	1.	.pva file – virtual asset
	2.	.pvadd file - deployment details if deploy option in step 3 is set to false 
	3.	.pmpdd file – proxy (optional).
2.	Git repositories use webhooks to trigger build/test jobs – i.e. Jenkins, Ado, gitlab, etc
3.	The job will pull a SOAvirt docker conatainer, license it, and deploy the assets in /virt folder.
   	- The job needs to call the soavirt server API to upload the file, with two optional flags: deploy=true or false; replace=true or false.
	- See:  POST /v6/files/upload on the <host>:<port>/soavirt/api REST API page for additional documentation regarding this API call.
4.	After that you run you validation or repeat step 3 for any additional servers.

## Project Structure

```
.
+-- virt
|   +-- HelloWorld.pva
|   +-- HelloWorld.pvadd
+-- .gitignore
+-- README.md
+-- azure-pipelines.yaml
``` 

