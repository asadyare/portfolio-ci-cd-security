# Reusable CI and Security Workflows

[![Daily Security](https://github.com/asadyare/portfolio-daily-security/actions/workflows/security-alerting-and-reporting.yml/badge.svg)](https://github.com/asadyare/portfolio-daily-security/actions/workflows/security-alerting-and-reporting.yml)

![Weekly Report](https://img.shields.io/badge/reporting-weekly-blue)

![Alerting](https://img.shields.io/badge/alerting-critical--only-red)

## Overview

This repository acts as the shared CI and security control plane for the portfolio. It provides reusable workflows consumed by application and infrastructure repositories to enforce security controls consistently.

### Central Security Model

This repository focuses on security at pull request and deployment time. Ongoing and post merge security monitoring is handled by a dedicated daily security repository.

### Security Responsibilities

- CI and Deployment Security
- Pull request security scanning
- Deployment time container and dependency checks
- Reusable workflows enforced via workflow calls

### Post Merge and Continuous Security

Daily and weekly security monitoring runs outside CI pipelines
Critical findings trigger automatic alerts
Weekly security posture reports provide governance visibility

### Daily and Weekly Security Integration

Continuous security monitoring is implemented in the portfolio-daily-security repository.
This model ensures newly disclosed vulnerabilities are detected even when no code changes occur.

#### Daily scans

Run on a fixed schedule
Detect new CVEs, dependency disclosures, and container risks

#### Alerting

Critical findings automatically create GitHub Issues
Alerts link directly to scan evidence

#### Weekly reporting

A weekly security report issue summarises coverage and execution
Provides a clear audit trail for reviewers

## Purpose

The goal of this repository is to enforce security by default across all projects. Any repository consuming these workflows inherits the same security standards without copying logic or configuration.

- Core Capabilities
- Secret scanning across source code and commits
- Static application security testing for application code
- Dependency vulnerability scanning
- Container image scanning during build pipelines
- Fail fast enforcement for pull requests and main branch deployments
- Reusable workflows consumed through workflow_call

## Architecture Model

This repository functions as a shared security center. Downstream repositories trigger workflows from this repo instead of defining security logic locally. Results and evidence remain visible in the calling repository Actions logs.

### Diagram

CI and Security Architecture Diagram
[![CI/CD Security Architecture](diagrams/architecture.png)](diagrams/architecture.png)

## Connected Repositories

1. [Frontend application](https://github.com/asadyare/portfolio-frontend)

2. [Kubernetes Deployment and security](https://github.com/asadyare/portfolio-k8s-microservices-deployment)
3. [Daily security automation](https://github.com/asadyare/portfolio-daily-security)

Workflow Consumption Pattern
Repositories invoke shared workflows using GitHub Actions workflow calls.
Security logic executes centrally.
Results propagate back to the caller pipeline.
Failed checks block merge or deployment.

## Central Portfolio Reference

Primary portfolio index and documentation
[Central reposittory](https://github.com/asadyare/devsecops-portfolio-asad)

Operational Benefits
Single place to update security tooling
Consistent enforcement across projects
Clear audit trail inside GitHub Actions
Reduced configuration drift
Portfolio wide security posture visibility

## Contact

You can contact me via [walasaqo@gmail.com](mailto:walasaqo@gmail.com) or connect with me on [LinkedIn](https://www.linkedin.com/in/asad-hassan-20b540313/).

## License

This portfolio is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
