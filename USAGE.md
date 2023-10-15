# Usage Guide

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Configuration](#configuration)
- [Command-Line Options](#command-line-options)
- [Error Handling](#error-handling)
- [Contributing](#contributing)
- [Support](#support)

## Introduction

`auto-commit-msg` is a utility designed to automatically generate semantic commit messages based on the content of your commits. This document aims to guide you through its usage.

## Installation

Please refer to the `INSTALL.md` file for installation instructions.

## Configuration

Before using `auto-commit-msg`, you need to configure it. Run the following command to start the configuration process:

```bash
auto-commit-msg -c
```

This will prompt you for your OpenAI API key and other preferences.

## Command-Line Options

- `-i [path]`: Install the commit-msg hook in the specified Git project directory.
- `-u [path]`: Update the commit-msg hook in the specified Git project directory.
- `-c`: Configure your OpenAI API key.
- `-h`: Display help information.
- `--u`: User-level configuration.
- `--p`: Project-level configuration.

## Error Handling

The utility provides detailed error messages for various issues. Each error message includes:

- The reason for the error.
- Steps for the user to fix the issue.
- How to contribute if you believe it's a bug.
- How to seek community or professional support.

## Contributing

If you would like to contribute to the project, please refer to the `CONTRIBUTING.md` file for guidelines.

## Support

For professional support, please contact `ricardomalnati@gmail.com`. For community support, you can post questions on Stack Overflow with the tag `auto-commit-msg`.
