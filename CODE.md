# Consolidated Coding Conduct Guide with Examples and References

## Table of Contents

1. [Confirmations](#confirmations)
1. [Regex](#regex)
1. [Agnosticism](#agnosticism)
1. [Preferences](#preferences)
1. [Debug Messages](#debug-messages)
1. [Error Messages](#error-messages)
1. [Error Numbering](#error-numbering)
1. [Variables](#variables)
1. [Parameters](#parameters)
1. [Syntax](#syntax)
1. [Header](#header)

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
### Checklist for Variables

- Are the variable names descriptive?
- Are environment variables in uppercase?
- Are script-level variables in lowercase?
- Are the variables well-commented to indicate their purpose?
- Are the spelling correct?
- Are the variable addressed by Parameter Expansion: ${VARIABLE} istead of Simple Variable Expansion: "$VARIABLE"? The ${VARIABLE} syntax is beneficial for more advanced operations. Recommending its use over "$VARIABLE" could lead to more maintainable and flexible code.

This checklist and the automated verification parameters should help in ensuring that the Bash Script code adheres to best practices for variable naming and commenting.

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the use of variables. Ensure that variable names are descriptive and improve code readability and maintainability. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check if the variables follow the guidelines: Are the variable names descriptive? Are variables in uppercase and function-level variables in lowercase? Are the variables well-commented to indicate their purpose? Are the variable addressed by Parameter Expansion: ${VARIABLE} istead of Simple Variable Expansion: "$VARIABLE"? Are the spelling correct?: [Insert Bash Script Code Here]
```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the use of variables. Ensure that variable names are descriptive and improve code readability and maintainability. Provide a revised version of the code that aligns with these guidelines."
--arg user_content "Please analyze the code to check if the variables follow the guidelines: Are the variable names descriptive? Are variables in uppercase and function-level variables in lowercase? Are the variables well-commented to indicate their purpose? Are the spelling correct? Are the variable addressed by Parameter Expansion: ${VARIABLE} istead of Simple Variable Expansion: "$VARIABLE"? : [Insert Bash Script Code Here]"
```

### Reference
- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html#s7.1-variable-names)

---
## Parameters

### Rationale
Parameters provide a way to customize the behavior of a script. They make the script more flexible and easier to use in different scenarios.

## Guidelines for Creating Parameters

### Descriptive Names
- Use descriptive names for parameters to clarify their functionality.

### Scope Parameters
- Provide a `--local` parameter for project-level configurations.
- Provide a `--global` parameter for user-level configurations at `~/`.

### Default Values
- Set sensible default values for optional parameters.

### Validation
- Validate parameter values at the beginning of the script to prevent errors.

### Example
```bash
# Parsing parameters
while [[ "$#" -gt 0 ]]; do
  case $1 in
    -l|--local) local_dir="$2"; shift ;;
    -g|--global) global_dir="$2"; shift ;;
    -d|--debug) debug=true ;;
    *) echo "Unknown parameter: $1"; exit 1 ;;
  esac
  shift
done
```

## Checklist for Parameters (Without Guidelines)

1. Is the parameter name self-explanatory?
2. Are both short (`-l`) and long (`--local`) options available?
3. Are default values specified for optional parameters?
4. Is early validation performed for parameter values?
5. Does the `--local` parameter affect only the project-level settings?
6. Does the `--global` parameter affect only the user-level settings?
7. Are (`-d`) and (`--debug`) options available?

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on parameters, their scope, default values, and validation. Ensure the code readability and maintainability. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check it follows the guidelines: 
> - Is the parameter name self-explanatory?
> - Are both short (-l) and long (--local) options available?
> - Are default values specified for optional parameters?
> - Is early validation performed for parameter values?
> - Does the --local parameter affect only the project-level settings? The --local parameter must be optional and it is the default scope.
> - Does the --global parameter affect only the user-level settings? The --global parameter must be optional.
> - Are (`-d`) and (`--debug`) options available? [Insert Bash Script Code Here]"

```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on parameters, their scope, default values, and validation. Ensure the code readability and maintainability. Provide a revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check it follows the guidelines: 
- Is the parameter name self-explanatory?
- Are both short (-l) and long (--local) options available?
- Are default values specified for optional parameters?
- Is early validation performed for parameter values?
- Does the --local parameter affect only the project-level settings?
- Does the --global parameter affect only the user-level settings?
- Are (`-d`) and (`--debug`) options available?" [Insert Bash Script Code Here]"
```

### References
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#Shell-Parameters)
- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html#s5.1-issues-with-flags)
- [Git Config Documentation](https://git-scm.com/docs/git-config)
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

### Checklist for Debug Messages

- Is the debug flag (`$DEBUG`) used to control the display of debug messages?
- Are debug messages clearly labeled with a "Debug:" prefix?
- Are sensitive or private information excluded from debug messages?
- Are debug messages optional and controlled by a flag or environment variable?
- Are there non sensible variables and parameters in the messages? 

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the use of debug messages. Ensure that debug messages assist in troubleshooting and are optional. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check if the debug messages follow the guidelines: Is the debug flag used to control the display of debug messages? Are debug messages clearly labeled with a 'Debug:' prefix? Are sensitive or private information excluded from debug messages? Are there non sensible variables and parameters in the messages? Are debug messages optional and controlled by a flag or environment variable?:

```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the use of debug messages. Ensure that debug messages assist in troubleshooting and are optional. Provide a revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if the debug messages follow the guidelines: Is the debug flag used to control the display of debug messages? Are debug messages clearly labeled with a 'Debug:' prefix? Are sensitive or private information excluded from debug messages? Are there non sensible variables and parameters in the messages? Are debug messages optional and controlled by a flag or environment variable?: [Insert Bash Script Code Here]"
```

### Reference
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#The-Set-Builtin)

---
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

### Developer's Checklist for Crafting Error Messages

- Is the message clear and free from jargon or complex terms?
- Does the message have a logical flow?
- Does the message provide actionable steps or suggestions?
- Is the tone of the message positive and nonjudgmental?
- Does the message avoid blaming the user?
- Is humor or sarcasm absent from the message?

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the crafting of error messages. Ensure that error messages are clear, actionable, and maintain a positive tone. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check if the error messages follow the guidelines: Is the message clear and free from jargon or complex terms? Does the message have a logical flow? Does the message provide actionable steps or suggestions? Is the tone of the message positive and nonjudgmental? Does the message avoid blaming the user? Is humor or sarcasm absent from the message?: 

```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the crafting of error messages. Ensure that error messages are clear, actionable, and maintain a positive tone. Provide a revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if the error messages follow the guidelines: Is the message clear and free from jargon or complex terms? Does the message have a logical flow? Does the message provide actionable steps or suggestions? Is the tone of the message positive and nonjudgmental? Does the message avoid blaming the user? Is humor or sarcasm absent from the message?: [Insert Bash Script Code Here]"
```

### Reference
- [Microsoft's Guidelines for Error Messages](https://docs.microsoft.com/en-us/windows/win32/uxguide/mess-error)
- [Apple's Human Interface Guidelines: Handling Errors](https://developer.apple.com/design/human-interface-guidelines/macos/user-interaction/handling-errors/)
- [Microsoft's Best Practices for Writing Error Messages](https://docs.microsoft.com/en-us/windows/win32/debug/writing-error-messages)

---
## Confirmations

### Reason

Confirmation checks are essential for validating that previous operations in the code have executed successfully and without errors. These checks enhance the robustness and reliability of the script.

### Guide

1. **Explicit Checks**: Implement explicit checks after each critical operation to confirm its successful execution.
2. **Error Handling**: Include checks for error messages or error numbers to ensure the operation did not fail.
3. **Validation**: Confirm the intended effect of the operation, such as verifying that a file has been deleted.

### Example

```bash
# Delete a file and confirm its deletion
rm -f /path/to/file
if [ $? -eq 0 ] && [ ! -f /path/to/file ]; then
  echo "File successfully deleted."
else
  echo "File deletion failed."
fi
```

### Situations for Use

- After file operations like creation, deletion, or modification to confirm their successful execution.
- Following API calls to validate both the call and the expected outcome.
- After setting environment variables or changing system settings to confirm they have been applied.

### Developer's Checklist for Confirmations

- Are all operations followed by confirmation checks?
- Do the confirmation checks include error handling, such as error messages or error numbers?
- Do the confirmation checks validate the intended effect of the operation?
- Are the confirmation checks well-documented to indicate their purpose?

### Reference

- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)

### Automated Verification with AI

> You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on confirmation checks after each operation, not just critical operations. Ensure that all operations are followed by confirmation checks and that these checks validate the success of the operation.
> Provide a full file revised version of the code that aligns with these guidelines. The guidelines: Are all operations followed by confirmation checks? Do the confirmation checks include error handling? Do the confirmation checks validate the intended effect of the operation? When it is about file operations, it's not only to check the file itself but the properties of the file to expose in the message:

```bash
--arg sys_content "You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on confirmation checks after each operation, not just critical operations. Ensure that all operations are followed by confirmation checks and that these checks validate the success of the operation."

--arg user_content "Provide a full file revised version of the code that aligns with these guidelines. The guidelines: Are all operations followed by confirmation checks? Do the confirmation checks include error handling? Do the confirmation checks validate the intended effect of the operation? When it is about file operations, it's not only to check the file itself but the properties of the file to expose in the message: [Insert Bash Script Code Here]"
```

### References

- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)

---
## Error Numbering

### Reason

Error numbering facilitates debugging and improves the quality of documentation. Each unique error should have a unique number to prevent confusion and make it easier to investigate issues.

### Guide

1. **Uniqueness**: Ensure that each error number is unique and not reused for different errors.
2. **Documentation**: Document each error number along with its corresponding message and possible resolution steps.
3. **Consistency**: Use a consistent numbering scheme, such as starting from 100 for file-related errors, 200 for network-related errors, etc.

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

### Developer's Checklist for Crafting Error Numbering

- Is each error number unique?
- Is each error number documented along with its message and possible resolution?
- Is a consistent numbering scheme used?

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on error numbering. Ensure that each error number is unique, documented, and follows a consistent numbering scheme. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check if the error numbering follows the guidelines: Is each error number unique? Is each error number documented along with its message and possible resolution? Is a consistent numbering scheme used?: 

```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on error numbering. Ensure that each error number is unique, documented, and follows a consistent numbering scheme. Provide a revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if the error numbering follows the guidelines: Is each error number unique? Is each error number documented along with its message and possible resolution? Is a consistent numbering scheme used?: [Insert Bash Script Code Here]"
```

### References

- [Microsoft's Guidelines for Error Handling](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design#error-return-codes)

---

## Syntax

### Reason

Following a consistent syntax is crucial for code readability, maintainability, and collaboration. It ensures that the code adheres to best practices and is easy to understand for anyone who reads it.

### Guide

1. **Consistency**: Always use the same coding style and conventions throughout the script.
2. **Comments**: Use comments to explain complex or non-intuitive code blocks.
3. **Indentation**: Use consistent indentation to improve code readability.

### Example

```bash
# Bash example for consistent syntax
if [ "$var" == "true" ]; then
  echo "Condition met."
else
  echo "Condition not met."
fi
```
Certainly, Ricardo. Below are the details you requested:

### Developer's Checklist for Syntax

- Is the coding style and conventions consistent throughout the script?
- Are comments used to explain complex or non-intuitive code blocks?
- Is consistent indentation applied for better code readability?

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on syntax. Ensure that the code is consistent in style, well-commented, and uses proper indentation. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check if the syntax follows the guidelines: Is the coding style and conventions consistent throughout the script? Are comments used to explain complex or non-intuitive code blocks? Is consistent indentation applied?:

```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on syntax. Ensure that the code is consistent in style, well-commented, and uses proper indentation. Provide a revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if the syntax follows the guidelines: Is the coding style and conventions consistent throughout the script? Are comments used to explain complex or non-intuitive code blocks? Is consistent indentation applied?: [Insert Bash Script Code Here]"
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

### Developer's Checklist for Header

- Is the header present at the top of the script?
- Does the header include the script name?
- Is the author's name specified?
- Is the creation date mentioned?
- Does the header provide a brief description of the script's purpose?
- Are any dependencies listed?
- Are limitations, such as OS compatibility, clearly stated?

### Automated Verification with AI

> You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the header section. Ensure that the header is present and includes all mandatory fields like script name, author, creation date, description, dependencies, and limitations. Provide a revised version of the code that aligns with these guidelines.
> Please analyze the code to check if the header follows the guidelines: Is the header present at the top of the script? Does it include the script name, author, creation date, description, dependencies, and limitations?: 

```bash
--arg sys_content "You are tasked with reviewing a Bash Script code to ensure it adheres to the specified coding conduct guidelines. Specifically, focus on the header section. Ensure that the header is present and includes all mandatory fields like script name, author, creation date, description, dependencies, and limitations. Provide a revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if the header follows the guidelines: Is the header present at the top of the script? Does it include the script name, author, creation date, description, dependencies, and limitations?: [Insert Bash Script Code Here]"
```

### References

- [Apple's Shell Scripting Primer](https://developer.apple.com/library/archive/documentation/OpenSource/Conceptual/ShellScripting/Introduction/Introduction.html)

---

## Agnosticism

### Reason

Code should be as agnostic as possible to ensure compatibility across different environments. The primary focus should be on compatibility with Linux and macOS when using Bash scripts.

### Guide

1. **OS Compatibility**: Always check for OS compatibility.
2. **Bash Version**: Make sure the script is compatible with biult-in Bash.

### Example

```bash
# Determine the home directory in a way that's compatible with both Linux and macOS
HOME_DIR=$(eval echo ~$USER)
```

### Developer's Checklist for Agnosticism

- Is the code compatible with both Linux and macOS?
- Does the code adhere to Bash best practices?
- Is the script built-in Bash commands only?

### Automated Verification with AI

> You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on agnosticism. Ensure that the code is compatible with both Linux and macOS and adheres to Bash best practices. Provide a full-file revised version of the code that aligns with these guidelines. Please analyze the code to check if it follows the guidelines for agnosticism: Is the code compatible with both Linux and macOS? Does it adhere to Bash best practices? Is the script built-in Bash commands only?
[Insert Bash Script Code Here]

```bash
--arg sys_content "You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on agnosticism. Ensure that the code is compatible with both Linux and macOS and adheres to Bash best practices. Provide a full-file revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if it follows the guidelines for agnosticism: Is the code compatible with both Linux and macOS? Does it adhere to Bash best practices? Is the script built-in Bash commands only? [Insert Bash Script Code Here]"
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

### Example

```bash
# ~/.my_preferences for global preferences
export DEBUG=true

# ./.my_preferences for local preferences
export DEBUG=false
```
Certainly, Ricardo. Here are the details you requested:

### Developer's Checklist for Preferences

- Are preferences stored in dot files?
- Is there an option for both global (`--global`) and local (`--local`) preferences?

### Automated Verification with AI

> You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on preferences. Ensure that preferences are easily configurable and stored in dot files, either at the user level (--global) or at the project level (--local). Provide a full-file revised version of the code that aligns with these guidelines.
> Please analyze the code to check if it follows the guidelines for preferences: Are preferences stored in dot files? Is there an option for both global (--global) and local (--local) preferences?:
[Insert Bash Script Code Here]

```bash
--arg sys_content "You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on preferences. Ensure that preferences are easily configurable and stored in dot files, either at the user level (--global) or at the project level (--local). Provide a full-file revised version of the code that aligns with these guidelines."

--arg user_content "Please analyze the code to check if it follows the guidelines for preferences: Are preferences stored in dot files? Is there an option for both global (--global) and local (--local) preferences?: [Insert Bash Script Code Here]"
```

### Reference

- [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html#Bash-Startup-Files)

---

## Regex

### Reason

Regular expressions in Bash should be the priority for dynamic matching. This ensures better performance and maintainability.

### Guide

1. **Regular Expressions**: Use Bash's built-in regular expression support whenever possible.
2. **Fallback**: Use `grep` only when the required functionality is not supported by Bash.

### Example

```bash
# Using Bash's built-in regular expression support
if [[ $string =~ ^[0-9]+$ ]]; then
  echo "It's a number."
fi
```
Certainly, Ricardo. Below are the details you requested:

### Developer's Checklist for Dynamic Matching

- Are regular expressions used for dynamic matching?
- Is `grep` used only as a fallback?

### Automated Verification with AI

> You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on dynamic matching using regular expressions. Ensure that regular expressions are the priority for dynamic matching for better performance and maintainability.
> Provide a full-file revised version of the code that aligns with these guidelines. Please analyze the code to check if it follows the guidelines for dynamic matching: Are regular expressions used for dynamic matching? Is grep used only as a fallback.
> [Insert Bash Script Code Here]

```bash
--arg sys_content "You are code fixing script that ensures the inputted code adheres to the specified coding conduct guidelines. Specifically, focus on dynamic matching using regular expressions. Ensure that regular expressions are the priority for dynamic matching for better performance and maintainability."

--arg user_content "Provide a full-file revised version of the code that aligns with these guidelines. Please analyze the code to check if it follows the guidelines for dynamic matching: Are regular expressions used for dynamic matching? Is grep used only as a fallback. [Insert Bash Script Code Here]"
```

### Reference

- [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
