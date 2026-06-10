# Security Scanning Pipeline

## Summary

Security scanning pipeline for .NET and NodeJS projects.
- Frontend: npm audit report - published to artifacts.
- Frontend: Retire.js scan - published to artifacts.
- Backend: Semgrep scan
- Backend: Gitleaks scan - published to artifacts.
- Backend: OWASP dependency scan - published to artifacts.

## Prerequisites

For the .NET scan your pipeline will need to have access to the `SecurityVariables` variable group, which holds the `NVD_API_KEY`.

## Version

![dotnet 8](https://img.shields.io/badge/net8.0-blue.svg)

## Setup Instructions

1. Go to  [Azure DevOps](https://dev.azure.com/tbs-sct/GCExchange/_build) and create a new pipeline.
2. Connect to the repository in either GitHub or Azure Repos Git.
3. Configure the pipeline to any template, we will replace the code so it doesn't matter.
4. On the review step replace the code with either `frontend.yml` or the `backend.yml` file, depending on if the project is nodeJS or .Net.
5. Rename the yml file to `security-pipeline.yml` in the UI.
6. If the project is .Net and you're using the `backend.yml` you will need to give the pipeline permission to use the `SecurityVariables` variable group.

## Ignore Packages (Frontend Only)

Follow these steps to ignore specific npm packages during the npm audit.

1. Add a file named `ignored-packages.txt` in the same directory as your .yml file.
2. Add each package that should be ignored on its own line within the file.
3. Save and run the pipeline.
<img width="235" height="183" alt="image" src="https://github.com/user-attachments/assets/c4e223b6-af71-4736-a061-07ce05e1f180" />


