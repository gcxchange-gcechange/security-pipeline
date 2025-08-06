# Security Scanning Pipeline

## Summary

Security scanning pipeline for .NET and NodeJS projects.
- Frontend: npm audit report - published to artifacts.
- Frontend: Retire.js scan - published to artifacts.
- Backend: Semgrep scan
- Backend: Gitleaks scan - published to artifacts.
- Backend: OWASP dependency scan - published to artifacts.

## Prerequisites

You will need to setup a pipeline secret variable named `NVD_API_KEY` to run the OWASP dependency scan.
You can request a key [here](https://nvd.nist.gov/developers/request-an-api-key).

## Version

![dotnet 8](https://img.shields.io/badge/net8.0-blue.svg)

## Setup Instructions

1. Go to  [Azure DevOps](https://dev.azure.com/tbs-sct/GCExchange/_build) and create a new pipeline.
2. Connect to the repository in either GitHub or Azure Repos Git.
3. Configure the pipeline to any template, we will replace the code so it doesn't matter.
4. On the review step replace the code with ether `frontend-scan.yml` or the `backend-scan.yml` file, depending on if the project is nodeJS or .Net.
5. If the project is .Net and you're using the `backend-scan.yml` you need to setup a new variable for the pipeline. The variable name should be `NVD_API_KEY` and set to secret. The value should be the API key for OWASP dependency scan which you can request [here](https://nvd.nist.gov/developers/request-an-api-key).
<img width="722" height="920" alt="image" src="https://github.com/user-attachments/assets/597a1d03-c754-405e-b1bf-5c8db3a8b916" />

## Ignore Packages (Frontend Only)

1. Add a file named `ignored-packages.txt` in the same directory as your .yml file.
2. Add each package that should be ignored on its own line within the file.
3. Save and run the pipeline.

