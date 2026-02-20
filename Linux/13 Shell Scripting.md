Here are short and meaningful answers for each of your questions:

## 1. **What is bash?**

* **Bash** (Bourne Again Shell) is a command-line interpreter and scripting language used in Linux and UNIX-based systems for executing commands and writing shell scripts.

## 2. **What are environment variables?**

* **Environment variables** are dynamic values that affect the behavior of processes. Examples include `HOME`, `USER`, and `PATH`, which store system settings and user-specific information.

## 3. **What is PATH?**

* **PATH** is an environment variable that contains a colon-separated list of directories where executable programs are located. It helps the system locate commands without needing full paths.

## 4. **Special variables ($0, $1, $?, $#)?**

* `$0`: The name of the script.
* `$1`, `$2`, etc.: Positional parameters (arguments passed to the script).
* `$?`: Exit status of the last command executed.
* `$#`: Number of arguments passed to the script.

## 5. **Difference between single quotes ' and double quotes " in scripts?**

* **Single quotes ('')** preserve the literal value of characters, meaning no variable substitution.
* **Double quotes ("")** allow variable and command substitution inside the quotes.

## 6. **What are loops in shell?**

* **Loops** (like `for`, `while`, `until`) allow repeated execution of commands or actions based on conditions, improving script efficiency.

## 7. **What are condition statements?**

* **Condition statements** (`if`, `else`, `elif`) are used to execute commands based on test results or conditions.

## 8. **How to pass arguments to a script?**

* Arguments are passed to a script by adding them after the script name when executing, e.g., `./script.sh arg1 arg2`. Inside the script, you can access them via `$1`, `$2`, etc.

## 9. **How to schedule recurring jobs with at command?**

* The `at` command schedules a one-time job at a specific time. Example: `echo "command" | at 2pm` runs the command at 2 PM.

## 10. **What are cron jobs?**

* **Cron jobs** are scheduled tasks that run automatically at specified intervals (e.g., daily, weekly) using the `cron` daemon.

## 11. **Fields of cron?**

* A **cron expression** has 5 fields:
  `* * * * *`
  `| | | | |`
  `| | | | +---- Day of week (0 - 7)`
  `| | | +------ Month (1 - 12)`
  `| | +-------- Day of month (1 - 31)`
  `| +---------- Hour (0 - 23)`
  `+------------ Minute (0 - 59)`

## 12. **What is crontab?**

* **Crontab** is a file that contains a list of cron jobs. It is used to schedule commands or scripts to run at specific times.

## 13. **Difference between $* and $@?**

* Both `$*` and `$@` represent all positional parameters, but:

  * **`$*`** treats all arguments as a single string (separated by the first character in `$IFS`).
  * **`$@`** treats each argument as a separate quoted string, preserving spaces.
