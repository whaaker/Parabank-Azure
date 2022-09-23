# Hello World

## Description
The following example demonstrates a job that creates an ephemeral Docker container in Azure and upload/deploys/replaces a pva on the server and runs a curl against it to validate it.

## Logical Flow

1.	User checks assets into SCM. Typically this is done via git commit/push/etc or EGit plugin for Eclipse.
a.	The user may check in any or all of the following:
i.	.pva file – virtual asset
ii.	.pvadd file - deployment details if deploy option in step 3 is set to false 
iii.	.pmpdd file – proxy.
2.	Git repositories use webhooks to trigger build/test jobs – i.e. Jenkins, Ado, gitlab, etc
3.	The job needs to call the soavirt server API to upload the file, with two optional flags: deploy=true or false; replace=true or false.
See:  POST /v6/files/upload on the <host>:<port>/soavirt/api REST API page for additional documentation regarding this API call.
4.	After that you run you validation or repeat step 3 for any additional servers.

## Project Structure

```
.
+-- virt
|   +-- hello_world.pva
|   +-- hello_world.pvadd
+-- .gitignore
+-- README.md
+-- azure-pipelines.yaml
``` 

