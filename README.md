# silver-waddle

Demo repository with comprehensive GitHub Actions workflows running on **arc-runner-set**.

## Workflows Overview

This repository contains 15+ demo/test workflows showcasing various GitHub Actions features:

### Basic Workflows

1. **01-hello-world.yml** - Simple workflow demonstrating basic job execution
   - Prints greeting messages
   - Shows runner information
   - Displays current date/time

2. **02-multiple-jobs.yml** - Demonstrates running multiple jobs in parallel
   - Three independent jobs running simultaneously
   - Shows parallel execution capabilities

3. **03-matrix-strategy.yml** - Matrix build strategy demonstration
   - Tests across multiple versions (1, 2, 3)
   - Tests across multiple environments (dev, staging, prod)
   - Total of 9 job combinations

### Advanced Workflows

4. **04-job-dependencies.yml** - Job dependency chain
   - Setup → Build → Test → Deploy pipeline
   - Passes outputs between jobs
   - Demonstrates sequential execution

5. **05-environment-variables.yml** - Environment variable usage
   - Global, job-level, and step-level variables
   - GitHub context variables
   - Variable scoping demonstration

6. **06-artifacts.yml** - Artifact upload and download
   - Creates build artifacts
   - Uploads artifacts for sharing
   - Downloads and verifies artifacts in dependent job

7. **07-caching.yml** - Dependency caching
   - Caches dependencies to speed up builds
   - Cache hit/miss detection
   - Demonstrates cache restoration

8. **08-conditional-execution.yml** - Conditional job and step execution
   - Event-based conditions (push, PR, workflow_dispatch)
   - Branch-based conditions
   - Workflow inputs with choices

### Operational Workflows

9. **09-scheduled-workflow.yml** - Cron-based scheduled execution
   - Daily execution at midnight UTC
   - Every 6 hours execution
   - Manual trigger support

10. **10-container-jobs.yml** - Container-based jobs
    - Jobs running in Docker containers
    - Service containers (Redis)
    - Container networking demonstration

11. **11-timeout-retry.yml** - Timeout and error handling
    - Job and step-level timeouts
    - Continue-on-error demonstration
    - Cleanup steps that always run

12. **12-checkout-git.yml** - Repository checkout operations
    - Basic checkout
    - Submodule checkout
    - Full history fetch
    - Git information display

### Control Workflows

13. **13-concurrency-control.yml** - Concurrency management
    - Workflow-level concurrency groups
    - Job-level concurrency groups
    - Cancel-in-progress configuration

14. **14-permissions.yml** - GitHub token permissions
    - Default permissions
    - Custom job permissions
    - No permissions configuration

15. **15-reusable-caller.yml** + **reusable-workflow.yml** - Reusable workflows
    - Calling reusable workflows
    - Passing inputs
    - Returning outputs
    - Secret inheritance

## Runner Configuration

All workflows in this repository are configured to run on:
```yaml
runs-on: arc-runner-set
```

## Triggers

Most workflows are triggered by:
- Push to `main` or `master` branches
- Pull requests to `main` or `master` branches
- Manual workflow dispatch

Some workflows have specialized triggers:
- **09-scheduled-workflow.yml**: Cron schedule
- **reusable-workflow.yml**: workflow_call event

## Usage

### Running Workflows Manually

1. Go to the "Actions" tab in GitHub
2. Select the workflow you want to run
3. Click "Run workflow"
4. Choose the branch and any required inputs
5. Click "Run workflow" button

### Testing Matrix Strategies

The matrix workflow (03) demonstrates running the same job with different parameters:
```yaml
strategy:
  matrix:
    version: [1, 2, 3]
    environment: [dev, staging, prod]
```

### Using Reusable Workflows

Call the reusable workflow from another workflow:
```yaml
jobs:
  call-workflow:
    uses: ./.github/workflows/reusable-workflow.yml
    with:
      environment: production
      version: "1.0.0"
```

## Features Demonstrated

- ✅ Basic job execution
- ✅ Multiple parallel jobs
- ✅ Matrix strategies
- ✅ Job dependencies and outputs
- ✅ Environment variables
- ✅ Artifact management
- ✅ Caching
- ✅ Conditional execution
- ✅ Scheduled/cron triggers
- ✅ Container jobs
- ✅ Service containers
- ✅ Timeout configuration
- ✅ Error handling
- ✅ Git operations
- ✅ Concurrency control
- ✅ Permission management
- ✅ Reusable workflows

## Architecture

All workflows are located in `.github/workflows/` and follow naming conventions:
- `01-` through `15-`: Numbered demo workflows
- `reusable-workflow.yml`: Shared reusable workflow

Each workflow is self-contained and can be studied independently.