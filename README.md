
# Jamatia's Mini OS Shell

Welcome to **Jamatia's Mini OS Shell**—a custom, interactive shell environment designed to simulate basic command-line operations for both Windows and Mac/Linux systems. This shell offers built-in commands, environment-specific functions, and session time-tracking, making it a unique utility for practicing and experimenting with common shell commands.

## Objective

The main objective of this project is to create a lightweight and interactive shell environment that simulates basic command-line functionality for both Windows and Mac/Linux operating systems. This shell will help users:

- Learn and practice essential shell commands used in different OS environments.
- Understand the behavior and syntax of various system-level commands.
- Experiment with file management, network utilities, and process control using a command-line interface.
- Track session time and gain insights into shell usage patterns.
- Provide an accessible platform for users to interact with and explore different operating system environments via a single shell interface.

## Technologies Used

- **C Programming Language**: The shell is implemented in C, providing low-level control over system processes.
- **Visual Studio Code**: Used as the primary Integrated Development Environment (IDE) for coding, debugging, and testing the Mini OS Shell.

## Key C Programming Concepts Demonstrated

This project highlights several important aspects of C programming, demonstrating both basic and advanced techniques:

### 1. **Standard Input/Output (I/O)**
   - **Usage of `printf` and `scanf`**: These functions are used to interact with the user, display information, and read user inputs. 
   - Example:
     ```c
     printf("Select environment (Windows/Mac/Linux): ");
     scanf("%s", environment);
     ```

### 2. **String Manipulation**
   - **Handling strings**: The project involves manipulating strings using C string functions like `strcpy`, `strlen`, and `strcmp`.
   - Example:
     ```c
     if (strcmp(command, "exit") == 0) {
         printf("Exiting the shell...\n");
         break;
     }
     ```

### 3. **Memory Management**
   - **Dynamic Memory Allocation**: `malloc` and `free` are used to allocate and deallocate memory dynamically for various data structures (like user inputs).
   - Example:
     ```c
     char *input = (char *)malloc(100 * sizeof(char));
     if (input == NULL) {
         printf("Memory allocation failed\n");
         exit(1);
     }
     free(input);
     ```

### 4. **Process Control**
   - **System Calls and `fork()`**: Using `fork()` to create new processes and `execvp()` to execute commands in a child process.
   - Example:
     ```c
     pid_t pid = fork();
     if (pid == 0) {
         execvp(command, args);  // Execute command in child process
     } else {
         wait(NULL);  // Parent waits for child process to finish
     }
     ```

### 5. **File I/O**
   - **File Operations**: Using `fopen()`, `fclose()`, `fread()`, and `fwrite()` to interact with files, simulating file navigation and management commands.
   - Example:
     ```c
     FILE *file = fopen("example.txt", "r");
     if (file != NULL) {
         fread(buffer, sizeof(char), 100, file);
         fclose(file);
     }
     ```

### 6. **Control Structures**
   - **Conditionals and Loops**: Mastery of `if`, `else`, `for`, and `while` loops to control program flow based on user inputs and command execution.
   - Example:
     ```c
     while (1) {
         printf("MiniShell> ");
         fgets(command, 100, stdin);
         if (strcmp(command, "exit") == 0) break;
     }
     ```

### 7. **Error Handling**
   - **Error Checking**: Proper error handling is implemented using `perror()` and checking return values of system calls and library functions.
   - Example:
     ```c
     if (system(command) == -1) {
         perror("Command execution failed");
     }
     ```

### 8. **Session Time Tracking**
   - **Time Functions**: Using the `time.h` library to track session time and display elapsed time after each command.
   - Example:
     ```c
     time_t start_time, end_time;
     time(&start_time);
     // Execute command...
     time(&end_time);
     printf("Time spent in shell: %.2f seconds\n", difftime(end_time, start_time));
     ```

---

## Features

- **Dual Environment Simulation**: Choose between Windows and Mac/Linux environments to simulate commands specific to each OS.
- **Command Execution**: Support for basic and system-level commands, including file navigation, directory management, and network utilities.
- **Elapsed Time Tracking**: Track and display time spent in the shell after each command, with a session summary upon exit.
- **Help System**: A built-in help command displaying a table of supported commands with examples for easy reference.

## Project Structure

The Mini OS Shell project is implemented in a single C file with easy-to-follow code that includes comments for better readability.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [Supported Commands](#supported-commands)
  - [Environment-Specific Commands](#environment-specific-commands)
  - [Command Examples](#command-examples)
- [Contributing](#contributing)
- [License](#license)

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/mini-os-shell.git
   cd mini-os-shell
   ```

2. Compile the shell program:
   ```bash
   gcc mini_os_shell.c -o mini_os_shell
   ```

3. Run the shell program:
   ```bash
   ./mini_os_shell
   ```

## Usage

When you run the shell, it will prompt you to select an environment:

- **Windows**: Simulates commands typically available on Windows.
- **Mac/Linux**: Simulates commands specific to Unix-like systems.

Once an environment is selected, the shell will display a welcome message, and you can start entering commands.

### Supported Commands

| Command            | Description                                         | Example                   |
|--------------------|-----------------------------------------------------|---------------------------|
| `help`             | Display help information with available commands    | `help`                    |
| `exit` / `quit`    | Exit the shell                                      | `exit`                    |
| `pwd`              | Print the current directory                         | `pwd`                     |
| `cd <dir>`         | Change directory                                    | `cd Documents`            |
| `ls` / `dir`       | List files and directories                          | `ls` or `dir`             |
| `clear`            | Clear the terminal screen                           | `clear`                   |
| `tree`             | Display directory structure                         | `tree`                    |
| `ipconfig` / `ifconfig` | Display network configuration info             | `ipconfig` or `ifconfig`  |
| `ping <host>`      | Check network connectivity                          | `ping google.com`         |
| `nslookup <host>`  | DNS lookup for hostname                             | `nslookup example.com`    |
| `traceroute` / `tracert` | Trace packet route to host                    | `traceroute example.com`  |
| `netstat`          | Display network connections and stats               | `netstat`                 |
| `curl <url>`       | Fetch data from specified URL                       | `curl http://example.com` |
| `hostname`         | Display the system hostname                         | `hostname`                |
| `mkdir <dir>`      | Create a new directory                              | `mkdir NewFolder`         |
| `rmdir <dir>`      | Remove an empty directory                           | `rmdir NewFolder`         |
| `rm <file>`        | Remove a file                                       | `rm file.txt`             |
| `ps`               | List running processes                              | `ps`                      |
| `kill <pid>`       | Terminate a process by process ID                   | `kill 1234`               |
| `top` / `tasklist` | Display active processes                            | `top` or `tasklist`       |
| `df` / `diskpart`  | Display disk usage and partition info               | `df` or `diskpart`        |
| `history`          | Display command history                             | `history`                 |

### Environment-Specific Commands

- **Windows Only**:
  - `dir`: Lists directory contents
  - `tasklist`: Shows all running processes
  - `diskpart`: Disk partition utility

- **Mac/Linux Only**:
  - `ls`: Lists directory contents
  - `ifconfig`: Displays network configuration
  - `top`: Displays active processes
  - `df`: Shows disk usage

### Command Examples

1. **Navigating Directories**:
   ```shell
   MiniShell> cd Documents
   ```

2. **Network Utility**:
   ```shell
   MiniShell> ping google.com
   ```

3. **Clearing the Screen**:
   ```shell
   MiniShell> clear
   ```

4. **Exit Shell**:
   ```shell
   MiniShell> exit
   ```

5

. **Help**:
   ```shell
   MiniShell> help
   ```

---

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any changes or improvements. You can also open an issue if you encounter any bugs or have feature requests.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This updated README reflects your C programming knowledge and highlights the various concepts you used in developing the Mini OS Shell project, providing a clear view of your capabilities with the language.
