# Hello World

## Description
The follwing repo demosntartes a repository flow which pushes the contents of the repo to a Docker SOAVirt Server, run validation then destroys it. Once the validation is complete the contents can be pushed to a prod server.

## Logical Flow

1. User cehcks assets into SC either via GUI or git bash 
2. The got repo triggers an ADO build. See: azure-pipelines.yaml
3. The ADO build pulls down a docker conatiner, licenses it, and uploads assets in /virt folder via /files/upload REST API
4. The buld runs a culr validation step and concludes.

## Project Structure

```
.
+-- tests
|   +-- test_hello_world.tst
+-- virt
|   +-- hello_world.pva
|   +-- hello_world.pvadd
|   +-- hello_world.pmpdd
+-- .gitignore
+-- README.md
+-- azure-pipelines.yaml
``` 

