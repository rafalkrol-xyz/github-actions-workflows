# GitHub Actions Workflows

## Overview

This repository is the home to various [GtiHub Actions (GHA) workflows](https://github.com/features/actions) that
[can be reused by across GitHub from other GHA workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows).

## Usage

You can call any of the workflows present in this repository by simply referencing them in your GitHub repository's GHA file, e.g.

```bash
# EXAMPLE FILE LOCATION WITHIN YOUR PROJECT: .github/workflows/YOUR_WORKFLOW_NAME.yml,
# NB check out the official docs for more: https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions#create-an-example-workflow

# EXAMPLE NAME
# NB check out the official docs for more: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#name
name: Docs & Changelog

# EXAMPLE WORKFLOW TRIGGER
# NB check out the official docs for more: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#on
on:
  push:
    branches:
      - main

# EXAMPLE USAGE OF REUSABLE WORKFLOWS
# NB the two jobs are run in sequence (one after the other) - check out the official docs for more: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idneeds
jobs:
  call-tf-docs-workflow:
    uses: rafalkrol-xyz/github-actions-workflows/.github/workflows/terraform_docs.yml@v1.1.2
  call-changelog-workflow:
    uses: rafalkrol-xyz/github-actions-workflows/.github/workflows/changelog.yml@v1.1.2
    needs: call-tf-docs-workflow
```
