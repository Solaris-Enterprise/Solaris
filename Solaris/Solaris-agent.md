Solaris-agent is a version-control driven remote access administration tool that utilizes modules to configure systems into desired states.

## Schema

```yaml
name: <task_name>         # The name of the task
kernel:                   # The operating system kernel
  type: <NT|Linux>        # Specify the kernel type: NT or Linux
actions:                  # List of actions to perform in the task
  - name: <action_name>   # Name of the action
    module: <module_name> # The module to execute
    arguments:            # Arguments for the module
      <argument_key>: <argument_value> # Specify key-value pairs for arguments
```

- A task is a YAML file that is to be interpreted on the agent machine.
- An action is a collection of modules that are to be executed on the agent machine.
- A module is a class that is pre-baked in the agent executable.
	- Arguments are to be determined by the module chosen.
### Example 

```yaml
name: Open and Screenshot
kernel:
  type: Linux
actions:
  - name: Open Browser
    module: open_browser
    arguments:
      url: "https://example.com"
  - name: Capture Screenshot
    module: screenshot
    arguments:
      output_path: ["/tmp/screenshot.png", "new entry"]
```

```yaml
name: Monitor System Health
kernel:
  type: NT
actions:
  - name: Log CPU Usage
    module: log_cpu
    arguments:
      interval: 10
      output_file: "C:\\system_logs\\cpu_log.txt"
  - name: Log Memory Usage
    module: log_memory
    arguments:
      interval: 10
      output_file: "C:\\system_logs\\memory_log.txt"
```
