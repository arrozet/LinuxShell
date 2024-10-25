# UNIX Shell Project

## Overview

This project implements a UNIX shell that serves as a command interpreter, acting as an interface between the user and the operating system. The shell is designed to read commands entered by the user, create processes to execute those commands, and manage job control for both foreground and background tasks.

### Project Foundation

The initial code provided for this project was incomplete and primarily included the following files:

- **Shell_project.c**: The main source file, which had a very basic loop for reading commands and executing them without proper error handling or job control.
- **job_control.c**: Contains functions related to job management but lacks full integration with the shell's functionalities.
- **job_control.h**: The header file that declares the functions and structures related to job management.
- **parse_redir.h**: Provides parsing capabilities for input/output redirection, which was a required feature of the basic shell.

This incomplete foundation served as the starting point for enhancing the shell, which was developed for the Operating Systems course at the University of Málaga.

### Development of the Basic Shell

The initial development of the basic shell focused on implementing fundamental functionalities, with particular attention to robustness and efficient memory management. The key features included:

- **Command Reading**: Capturing user input for command execution.
- **Process Creation**: Utilizing system calls such as `fork()` to create child processes for executing commands.
- **Execution of Commands**: Implementing `execvp()` to run external commands.
- **Job Control**: Basic handling of foreground and background jobs using `waitpid()` to manage process states.
- **Signal Handling**: Basic signal handling to manage child processes.



## Enhancements

The following enhancements were added to the shell to address the limitations of the original implementation:

1. **Respawnable Jobs**:
   - Implemented an internal command that allows jobs to run in a respawnable mode. If a respawnable job terminates, the shell automatically relaunches it.
   - Indicated by adding a `+` at the end of the command.
   - Modifications include:
     - Added a new state `RESPAWNABLE` to the `job_state` enumeration.
     - Updated the `job` structure to store process arguments for respawnable jobs.

2. **Alarm-Thread**:
   - Created a command to limit the lifetime of a job based on threads. After a specified time, if the job has not finished, it is killed using `SIGKILL`.

3. **Delay-Thread**:
   - Added an internal command to execute a command after a specified delay. The shell remains responsive during the delay period, allowing for additional commands.

4. **Signal Masking**:
   - Developed an internal command that allows specific signals to be masked during the execution of a command, preventing unwanted terminations.

## Usage

To compile and run the shell:

```bash
gcc Shell_project.c job_control.c -o shell
./shell
