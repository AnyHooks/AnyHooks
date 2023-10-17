# Consolidated Coding Conduct Guide with Examples and References

## Table of Contents

1. [Variables](#variables)
2. [Parameters](#parameters)
3. [Debug Messages](#debug-messages)
4. [Error Messages](#error-messages)
5. [Confirmations](#confirmations)
6. [Verifications](#verifications)
7. [Error Numbering](#error-numbering)
9. [Syntax](#syntax)
10. [Header](#header)
11. [Agnosticism](#agnosticism)
12. [Approaches](#approaches)
13. [Repeated Asking](#repeated-asking)

---

## Introduction

This document serves as a comprehensive guide for coding conduct, incorporating various aspects such as variables, debug messages, and more. It is designed to be adaptable across different projects and languages.

---

## Variables

### Reason
- Descriptive variable names improve code readability and maintainability.

### Example
```bash
API_KEY="your-api-key"  # Environment variable
user_input=""           # Script-level variable
```

### Reference
- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html#s7.1-variable-names)

---

## Parameters

### Rationale
Parameters provide a way to customize the behavior of a script. They make the script more flexible and easier to use in different scenarios.

### Guidelines for Creating Parameters

1. **Descriptive Names**: Use descriptive names for parameters to make it clear what they control.
2. **Short and Long Options**: Provide both short and long options for parameters.
3. **Default Values**: Set sensible default values for optional parameters.
4. **Validation**: Validate parameter values early in the script.

#### Example
```bash
# Parsing parameters
while [[ "$#" -gt 0 ]]; do
  case $1 in
    -l|--local) local="$2"; shift ;;
    -g|--global) global="$2"; shift ;;
    -d|--debug) debug=true ;;
    *) echo "Unknown parameter: $1"; exit 1 ;;
  esac
  shift
done
```

### Checklist for Parameters
- [ ] Is the parameter name descriptive?
- [ ] Are both short and long options provided?
- [ ] Are default values set for optional parameters?
- [ ] Is parameter validation performed?

### Automated Verification
To verify if your parameters adhere to these guidelines, you can use an automated verification process. Copy and paste the parameter-handling code snippet into the chat and request a line-by-line verification against the checklist.

#### How to Use
1. Copy the parameter-handling code snippet.
2. Paste it into the chat with ChatGPT.
3. Request a line-by-line verification against the checklist.

#### Example Request
To initiate the verification, you could say something like:

> Please analyze the code to check if the parameters follow the guidelines. Look for explicitness, default values, and validation:
```bash
# Parsing parameters
while [[ "$#" -gt 0 ]]; do
  case $1 in
    --local) local_flag=true;;
    --global) global_flag=true;;
    --debug) DEBUG=true;;
    *) echo "Unknown parameter passed: $1"; exit 1;;
  esac
  shift
done

# Default values
local_flag=${local_flag:-false}
global_flag=${global_flag:-false}
DEBUG=${DEBUG:-false}
```

### References
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#Shell-Parameters)
- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html#s5.1-issues-with-flags)
- [MIT's Missing Semester - Shell Tools](https://missing.csail.mit.edu/2020/shell-tools/)

---

## Debug Messages

### Reason
- Debug messages assist in troubleshooting and should be optional.

### Example
```bash
if [ "$DEBUG" == "true" ]; then
  echo "Debug: API call response - $API_RESPONSE"
fi
```

### Reference
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#The-Set-Builtin)

## Error Messages

### Reason
- Error messages should be clear, actionable, and nonjudgmental. They should guide the user toward resolving the issue without blaming them. Messages should also maintain a positive tone and avoid humor, as it can become stale if users encounter the error frequently.

### Guidelines for Crafting Error Messages
1. **Clarity**: The message should clearly indicate what went wrong.
2. **Actionable**: Provide steps or suggestions for resolving the issue. The priority is to guide the user on how they can resolve the issue independently. However, also mention that they can seek professional help, such as contacting system administrators or opening a support ticket.
3. **Community Support**: In open-source projects, guide the user to seek help from the community or developers on platforms like GitHub.
4. **Positive Tone**: Use a positive and nonjudgmental tone of voice.
5. **No Blame**: Avoid phrasing that blames users or implies they are doing something wrong.
6. **No Humor**: Avoid humor since it can become stale if users encounter the error frequently.

### Developer's Checklist for Crafting Error Messages
- [ ] Is the message clear and easily understandable?
- [ ] Does the message provide actionable steps or suggestions?
- [ ] Is the tone of the message positive and nonjudgmental?
- [ ] Does the message avoid blaming the user?
- [ ] Is humor or sarcasm absent from the message?

### Example
```bash
if [ -z "$API_KEY" ]; then
  echo "Oops! It looks like the API key is missing."
  echo "To resolve this, please set your API key and try again."
  echo "If you need further assistance, consider contacting your system administrator or opening a support ticket."
  echo "For open-source projects, you can also seek help from the community on GitHub."
  exit 1
fi
```

### Automated Checklist Verification
To ensure that your error messages adhere to the guidelines, you can use an automated verification process. Copy and paste the error message code snippet into the chat, and request a line-by-line verification against the checklist.

#### How to Use
1. Copy the error message code snippet.
2. Paste it into the chat with ChatGPT.
3. Request a line-by-line verification against the checklist.

This will allow you or another developer to quickly assess whether the error message meets the guidelines.

#### Example Request
To initiate the verification, you could say something like:

> Please verify the following error message code snippet against the error message checklist:
```bash
if [ -z "$API_KEY" ]; then
  echo "Oops! It looks like the API key is missing."
  echo "To resolve this, please set your API key and try again."
  echo "If you need further assistance, consider contacting your system administrator or opening a support ticket."
  echo "For open-source projects, you can also seek help from the community on GitHub."
  exit 1
fi
```

### Reference
- [Microsoft's Guidelines for Error Messages](https://docs.microsoft.com/en-us/windows/win32/uxguide/mess-error)
- [Apple's Human Interface Guidelines: Handling Errors](https://developer.apple.com/design/human-interface-guidelines/macos/user-interaction/handling-errors/)

---

## Confirmations

### Reason

Confirmation messages provide feedback to the user, indicating that an operation has been successfully completed.

### Guide

1. **Explicitness**: Make the confirmation message clear and to the point.
2. **Timing**: Display the confirmation message immediately after the successful completion of an operation.

### Checklist for Developers

- [ ] Is the confirmation message explicit and clear?
- [ ] Is the message displayed at the right time?

### AI-Based Code Verification

To verify if your confirmations adhere to these guidelines, you can use the following text to ask the AI:

> "Please analyze the code to check if the confirmation messages follow the guidelines. Look for explicitness and timing."

### Example

```bash
# Successful API call
if [ "$api_status" == "200" ]; then
  echo "API call successful."
fi
```

### Situations for Use

- After successful file operations (e.g., file creation, deletion).
- Upon successful API calls.
- After successful user authentication.

### References

- [Microsoft's Best Practices for Writing Error Messages](https://docs.microsoft.com/en-us/windows/win32/debug/writing-error-messages)

---
## Error Numbering

### Reason

Error numbering facilitates debugging and improves the quality of documentation. Each unique error should have a unique number to prevent confusion and make it easier to investigate issues.

### Guide

1. **Uniqueness**: Ensure that each error number is unique and not reused for different errors.
2. **Documentation**: Document each error number along with its corresponding message and possible resolution steps.
3. **Consistency**: Use a consistent numbering scheme, such as starting from 100 for file-related errors, 200 for network-related errors, etc.

### Checklist for Developers

- [ ] Is the error number unique?
- [ ] Is the error number documented?
- [ ] Does the error number follow the established numbering scheme?

### AI-Based Code Verification

To verify if your error numbering adheres to these guidelines, you can use the following text to ask the AI:

> "Please analyze the code to check if the error numbering follows the guidelines. Look for uniqueness, documentation, and consistency."

### Example

```bash
# File-related errors start from 100
FILE_NOT_FOUND=100
FILE_PERMISSION_DENIED=101

# Network-related errors start from 200
NETWORK_UNREACHABLE=200
API_CALL_FAILED=201

# Usage
echo "Error $FILE_NOT_FOUND: File not found."
```

### References

- [Microsoft's Guidelines for Error Handling](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design#error-return-codes)

---
Certainly, Ricardo. Below is the revised section for "Syntax" with the additional details you requested:

---

## Syntax

### Reason

Following a consistent syntax is crucial for code readability, maintainability, and collaboration. It ensures that the code adheres to best practices and is easy to understand for anyone who reads it.

### Guide

1. **Consistency**: Always use the same coding style and conventions throughout the script.
2. **Comments**: Use comments to explain complex or non-intuitive code blocks.
3. **Indentation**: Use consistent indentation to improve code readability.

### Checklist for Developers

- [ ] Is the code consistently styled?
- [ ] Are comments used to explain complex or non-intuitive parts?
- [ ] Is the indentation consistent?

### AI-Based Code Verification

To verify if your syntax adheres to these guidelines, you can use the following text to ask the AI:

> "Please analyze the code to check if the syntax follows the guidelines. Look for consistency, appropriate use of comments, and indentation."

### Example

```bash
# Bash example for consistent syntax
if [ "$var" == "true" ]; then
  echo "Condition met."
else
  echo "Condition not met."
fi
```

### References

- [Google's Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
- [Bash Best Practices by MIT](http://www.bash.academy/)
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#Syntax)

---

## Header

### Reason

A header is mandatory for every script as it provides essential metadata about the script, such as its purpose, author, and limitations. This information is crucial for understanding the script's context and dependencies.

### Guide

1. **Script Name**: Always specify the name of the script.
2. **Author**: Include the name of the author or authors.
3. **Creation Date**: Mention the date when the script was created.
4. **Description**: Provide a brief description of what the script does.
5. **Dependencies**: List any dependencies that the script relies on.
6. **Limitations**: Clearly state any limitations, such as OS compatibility.

### Checklist for Developers

- [ ] Is the header present at the top of the script?
- [ ] Does it include all the mandatory fields?
- [ ] Are the limitations clearly stated?

### AI-Based Code Verification

To verify if your script's header adheres to these guidelines, you can use the following text to ask the AI:

> "Please analyze the header of the code to ensure it contains all the mandatory fields like Script Name, Author, Creation Date, Description, Dependencies, and Limitations."

### Example

```bash
#!/bin/bash
# Script: rc/anyhooks
# Author: Ricardo Malnati
# Creation Date: 2023-10-15
# Description: Manages hooks, encryption, and language settings for AnyHooks
# Dependencies: rc/openaikey, rc/anyhookslang, rc/anyhooksver
# Limitations:  Linux, macOS
```

### References

- [Apple's Shell Scripting Primer](https://developer.apple.com/library/archive/documentation/OpenSource/Conceptual/ShellScripting/Introduction/Introduction.html)

---

## Agnosticism

### Reason

Code should be as agnostic as possible to ensure compatibility across different environments. The primary focus should be on compatibility with Linux and macOS when using Bash scripts.

### Guide

1. **OS Compatibility**: Always check for OS compatibility.
2. **Bash Version**: Make sure the script is compatible with different Bash versions.

### Checklist for Developers

- [ ] Is the code compatible with both Linux and macOS?
- [ ] Does it adhere to Bash best practices?

### AI-Based Code Verification

To verify if your script is OS-agnostic, you can use the following text to ask the AI:

> "Please analyze the code to ensure it is agnostic, focusing on compatibility with both Linux and macOS."

### Example

```bash
# Determine the home directory in a way that's compatible with both Linux and macOS
HOME_DIR=$(eval echo ~$USER)
```

### Reference

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#Bash-Startup-Files)

---

## Preferences

### Reason

Preferences should be easily configurable and stored in dot files, either at the user level (`--global`) or at the project level (`--local`).

### Guide

1. **Dot Files**: Use dot files to store preferences.
2. **Scope**: Allow for global (`--global`) and local (`--local`) preferences.

### Checklist for Developers

- [ ] Are preferences stored in dot files?
- [ ] Is there an option for global and local preferences?

### AI-Based Code Verification

To verify if your script handles preferences correctly, you can use the following text to ask the AI:

> "Please analyze the code to ensure it handles preferences correctly, focusing on storage in dot files and scope options."

### Example

```bash
# ~/.my_preferences for global preferences
export DEBUG=true

# ./.my_preferences for local preferences
export DEBUG=false
```

### Reference

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#Bash-Startup-Files)

---

## Approaches

### Reason
- Regular expressions in Bash should be the priority for dynamic matching

.

### Example
```bash
if [[ $string =~ ^[0-9]+$ ]]; then
  echo "It's a number."
fi
```

### Reference
- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html#s7-naming-conventions)

## Repeated Asking

### Reason
- Repeated asking of the same information should be avoided.

### Example
```bash
if [ -z "$user_input" ]; then
  read -p "Enter your input: " user_input
fi
```

### Reference
- [MIT Usability Guidelines](http://web.mit.edu/6.813/www/sp18/classes/05-user-testing/)