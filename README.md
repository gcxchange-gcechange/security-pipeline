# Security Scanning Pipeline

## Summary

Security scanning for C# and js/ts projects.
- Frontend scan on the condition that `package.json` or `tsconfig.json` are in the root directory.
- Backend scan on the condition that `*.csproj` or `*.sln` are in the root directory.
- Frontend: npm audit report - published to artifacts.
- Frontend: Retire.js scan - published to artifacts.
- Backend: Semgrep scan
- Backend: Gitleaks scan - published to artifacts.
- Backend: OWASP dependency scan - published to artifacts.

## Prerequisites

You will need to setup a build variable secret named `NVD_API_KEY` to run the OWASP dependency scan.
You can request a key [here](https://nvd.nist.gov/developers/request-an-api-key).

## Version

![dotnet 8](https://img.shields.io/badge/net8.0-blue.svg)
