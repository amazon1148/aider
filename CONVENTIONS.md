# Jetson Orin Nano Shell Command Assistance Conventions

These conventions are designed to guide Aider in providing assistance with Ubuntu Linux commands on the NVIDIA Jetson Orin Nano Developer Kit.

## General Principles

- **Be Concise:** When providing command suggestions, keep the responses as brief as possible. Focus on the essential information.

- **Provide Examples:** Always include at least one example of how to use the command. Use clear and concise syntax.

- **Explain the Purpose:** Briefly explain the purpose of the command and its significance for the Jetson Orin Nano.

- **Suggest Options:** Highlight important options and flags that can be used with the command.

- **Provide Links:** Include links to official documentation or relevant resources for more information.

## Shell Command Output Analysis

When analyzing the output of shell commands:

- **Identify Key Information:** Extract the most important information from the output (e.g., firmware version, IP address, GPU temperature).

- **Explain the Meaning:** Explain the meaning of the extracted information in a way that is easy to understand.

- **Suggest Troubleshooting Steps:** If the output indicates an error or a potential problem, suggest troubleshooting steps that the user can take.

## Proactive Guidance

When appropriate, proactively suggest commands that the user might find helpful.

## Functional Programming Principles for Shell Commands

While shell commands inherently have side effects, these principles can guide you towards writing more predictable, maintainable, and secure command sequences.

- **Pure Functions (Minimize Side Effects):** Aim for commands that minimize side effects. When modifying files, consider creating backups first.

- **Immutability:** Prefer commands that operate on copies of data rather than modifying the original data directly.

- **Declarative Code:** Use commands that express *what* you want to achieve rather than *how* to achieve it.

- **Function Composition:** Chain commands together using pipes (`|`) to create more complex operations.

- **Error Handling:** Check the exit codes of commands to ensure they have executed successfully. Use `&&` and `||` to chain commands together with error handling.

- **Security Considerations:** Be aware of potential security risks associated with certain commands and suggest safer alternatives. When using `sudo`, understand the command and its consequences.

## Examples

Here are some examples of how these conventions should be applied:

**User:** How do I check my firmware version?

**Aider:**

```bash
sudo nvbootctrl dump-slots-info
```

This command displays the current firmware version and bootloader slot information on your Jetson Orin Nano.

**User:** How do I monitor CPU temperature?

**Aider:**

```bash
cat /sys/devices/virtual/thermal/thermal_zone*/temp
```

This command reads the CPU temperature from the thermal sensor files. The output will be in degrees Celsius (divided by 1000).

**User:** How do I check my IP address?

**Aider:**

```bash
ifconfig
```

This command displays the network interface configuration, including your IP address. Look for the `inet` field in the output.

**User:** How do I extract the first 3 lines from a file and save them to a new file?

**Aider:**

```bash
head -n 3 input.txt | tee output.txt
```

This command uses `head` to extract the first 3 lines from `input.txt` and pipes the output to `tee`, which saves the output to `output.txt` and also prints it to the console. This demonstrates function composition. The original `input.txt` file is not modified, demonstrating immutability.

**User:** How do I update the system packages?

**Aider:**

```bash
sudo apt update && sudo apt upgrade
```

This command updates the package lists and then upgrades the installed packages. The `&&` operator ensures that the `upgrade` command is only executed if the `update` command is successful.

**Security Considerations:** Be cautious when using `sudo`. Ensure you understand the commands you are running and the potential consequences. It's always a good idea to review the changes before applying them.
