# GitHub Workflows

This directory contains GitHub Actions workflows for building and releasing the UserLAnd Android application.

## Workflows

### build-and-release.yml

This workflow builds the Android APK and handles releases. It triggers on:
- Push to `master` or `main` branches
- Push of version tags (e.g., `v1.0.0`)
- Manual workflow dispatch

#### Features

- **Build Types**: Supports both `beta` and `release` builds
- **APK Signing**: Uses GitHub secrets for secure signing
- **Artifact Upload**: Uploads APKs as GitHub artifacts
- **GitHub Releases**: Automatically creates releases for version tags
- **GitHub Pages**: Deploys APKs to GitHub Pages for easy download

## Required GitHub Secrets

To use the release functionality, you need to set up the following secrets in your GitHub repository:

1. Go to your repository settings
2. Navigate to "Secrets and variables" → "Actions"
3. Add the following repository secrets:

### Android Signing Secrets

- `ANDROID_KEY_ALIAS`: The alias of your signing key
- `ANDROID_STORE_PASSWORD`: The password for your keystore
- `ANDROID_KEY_PASSWORD`: The password for your signing key

### Keystore File

You also need to add your `keystore.jks` file to the repository root. This file should be:
- Named `keystore.jks`
- Placed in the root directory of the repository
- Used for signing both beta and release APKs

## Usage

### Automatic Builds

- **Push to main/master**: Automatically builds and uploads a release APK
- **Create a version tag**: Automatically creates a GitHub release with the APK

### Manual Builds

1. Go to the "Actions" tab in your repository
2. Select "Build and Release APK" workflow
3. Click "Run workflow"
4. Choose the build type (beta or release)
5. Click "Run workflow"

## Build Outputs

- **Artifacts**: APKs are uploaded as GitHub artifacts and can be downloaded from the Actions page
- **Releases**: For version tags, APKs are attached to GitHub releases
- **GitHub Pages**: For main/master pushes, APKs are deployed to GitHub Pages

## Notes

- The workflow uses Java 8 and Android SDK API level 30
- Gradle dependencies are cached for faster builds
- The workflow supports both debug and release configurations
- APK signing is required for release builds