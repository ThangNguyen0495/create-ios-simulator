# iOS Simulator UDID Action

The **iOS Simulator UDID Action** is a custom GitHub Action designed to automate the retrieval of the UDID for an iOS Simulator. This UDID is essential for configuring and running Appium tests for iOS applications.

## Features
- Installs Xcode command-line tools if not already installed.
- Configures the Xcode environment to use the correct version.
- Creates and boots an iOS Simulator (`iPhone-13` running `iOS 17.0`).
- Outputs the simulator's UDID to a `udid.txt` file, which can be used in subsequent steps or workflows.

## Requirements
- **Runner**: macOS (`macos-latest`).
- **Xcode**: Pre-installed on the GitHub Actions runner.

## Outputs
- **`udid.txt`**: A file containing the UDID of the created iOS Simulator.

## Usage

### Example Workflow
Here’s how you can integrate this action into your workflow:

```yaml
name: iOS Simulator UDID Workflow

on:
  workflow_dispatch:

jobs:
  ios-udid:
    runs-on: macos-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Retrieve iOS Simulator UDID
        uses: ./  # Path to the action's YAML file in your repository

      - name: View UDID
        run: cat udid.txt
