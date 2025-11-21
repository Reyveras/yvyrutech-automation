# YVYRUTECH Deployment Setup Guide

## Overview
This document provides step-by-step instructions to complete the deployment setup for the YVYRUTECH automation project.

## Prerequisites Completed
✓ Google Cloud Project created: `gen-lang-client-0139627197` (YVYRUTECH)
✓ Service Account created: `yvyrutech-automation`
✓ Google APIs enabled: Gmail API, Google Drive API
✓ Service Account Credentials downloaded: `gen-lang-client-0139627197-144066314fc4.json`
✓ GitHub Repository created: `Reyveras/yvyrutech-automation`
✓ GitHub Actions Workflow configured: `.github/workflows/deploy.yml`

## Next Steps - CRITICAL

### Step 1: Add Google Credentials Secret to GitHub

1. Go to: https://github.com/Reyveras/yvyrutech-automation/settings/secrets/actions
2. Click "New repository secret"
3. Name: `GOOGLE_CREDENTIALS_JSON`
4. Value: Copy the entire contents of the downloaded JSON file
   - File location: Your Downloads folder
   - Filename: `gen-lang-client-0139627197-144066314fc4.json`
5. Click "Add secret"

### Step 2: Verify Project Structure

The following files have been created:
- ✓ `.github/workflows/deploy.yml` - GitHub Actions workflow
- ✓ `requirements.txt` - Python dependencies
- ✓ `.gitignore` - Git ignore rules (auto-created)
- ✓ `LICENSE` - MIT License (auto-created)
- ✓ `README.md` - Project documentation (auto-created)

### Step 3: Push Code from Jules

The following files from Jules deliverables still need to be added:
- `main.py` - Main application entry point
- `src/yvyrutech.py` - Core automation logic
- `src/logger.py` - Logging configuration
- `src/config.py` - Configuration management
- `tests/test_*.py` - Test files
- `Dockerfile` - Docker configuration
- `docker-compose.yml` - Docker composition
- `k8s/*.yaml` - Kubernetes manifests

These can be added via:
- Direct file upload in GitHub UI
- Git CLI: `git clone`, add files, `git push`
- Jules integration after connecting

### Step 4: Trigger Workflow

Once the Google Credentials secret is added:
1. Push a commit to main branch (any change triggers the workflow)
2. Go to: https://github.com/Reyveras/yvyrutech-automation/actions
3. Monitor the workflow execution

## Environment Variables

The workflow uses the following secrets:
- `GOOGLE_CREDENTIALS_JSON` - Service Account credentials (JSON format)

These are automatically loaded by the workflow and available to the Python application.

## Troubleshooting

### Workflow Not Running
- Verify the secret `GOOGLE_CREDENTIALS_JSON` is added
- Check that the secret value is valid JSON
- Try pushing a new commit to trigger the workflow

### Authentication Errors
- Ensure the service account credentials are correct
- Verify the Gmail API is enabled in Google Cloud Console
- Verify the Google Drive API is enabled in Google Cloud Console
- Check that the service account has necessary permissions

## Security Notes

⚠️ IMPORTANT:
- Never commit the credentials JSON file to the repository
- Always use GitHub Secrets for sensitive data
- The credentials file is already in .gitignore
- Rotate credentials periodically

## Support

For issues or questions:
1. Check the workflow logs in GitHub Actions
2. Review the deployment guide
3. Check Google Cloud service account permissions
4. Verify all APIs are enabled in Google Cloud Console
