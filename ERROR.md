### Enhanced Error Message Requirements for the project

Below are the enhanced requirements for error messages in this project.

#### General Requirements

1. **Error Identification**
   - Each error should be identifiable with a unique exit code greater than 0.

2. **Message Clarity**
   - Error messages should be clear and concise, providing enough information to understand the issue.

#### Specific Requirements for Error Messages

1. **Reason for the Issue**
   - The message should clearly state why the error occurred, including any missing tasks from the user's side.
   - **Example**: "Error: Configuration file `~/.my-conf-file-rc` not found. Reason: The script requires this file for sourcing variables."

2. **Developer Guidance**
   - If the issue is not due to a missing user task, the message should guide developers on how to contribute to fixing the issue.
   - **Example**: "Developer Fix: If you believe this is a bug, please contribute by opening an issue on the GitHub repository."

3. **Support Service Guidance**
   - If the user has a support contract, the message should guide them on how to contact support.
   - **Example**: "Support: If you have a support contract, please contact support with error code 1."

4. **Community Help**
   - If no support is available and the issue is not due to a missing user task, the message should guide the user on how to seek community help.
   - **Example**: "Community Help: For community assistance, post your issue on Stack Overflow with the tag 'auto-commit-msg'. Suggested Question: 'How to resolve error code 1 in auto-commit-msg?'"

By adhering to these requirements, your project will offer a more user-friendly and developer-friendly experience, making it easier to diagnose issues, contribute to the project, and seek help when needed.