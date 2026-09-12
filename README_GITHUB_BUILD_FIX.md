# GitHub Build Fix

This package keeps the Stage 18 source project intact and updates the GitHub Actions workflow.

The repository does not include a Gradle Wrapper, so CI installs Gradle 8.11.1 directly and disables Gradle caching that expects gradle-wrapper.properties.

The workflow uses actions/setup-java@v5 and runs:
1. unit tests
2. Android lint
3. debug APK build
4. APK existence check
5. artifact upload

A real PASS still requires GitHub Actions and physical-device testing.
