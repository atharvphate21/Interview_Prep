## What is CLI and GUI?
In Linux, **CLI (Command-Line Interface)** allows users to interact with the system by typing commands in a terminal. **GUI (Graphical User Interface)** provides a visual interface with windows, icons, and menus for interaction. CLI is faster and more powerful for administration, while GUI is user-friendly.

## Helping commands in Linux?
In Linux, some helping commands provide information and guidance:

* `man command` – Shows the manual for a command.
* `--help` – Displays usage and options, e.g., `ls --help`.
* `info command` – Detailed documentation for commands.
* `whatis command` – Shows a short description of a command.
* `apropos keyword` – Searches commands related to a keyword.

These commands help learn and use Linux efficiently.

## What are standard streams?
In Linux, standard streams are the three default data channels used by programs:

* **stdin (0)** – Standard input, usually the keyboard.
* **stdout (1)** – Standard output, usually the terminal screen.
* **stderr (2)** – Standard error, used for error messages.

They allow input and output to be redirected or piped between commands.

## What are redirections?
In Linux, redirection is the process of sending input or output of a command to a file or another command instead of the default.

* `>` – Redirects output to a file (overwrite).
* `>>` – Redirects output to a file (append).
* `<` – Redirects input from a file.
* `2>` – Redirects error messages to a file.

Redirection helps save outputs or handle errors efficiently.

## What are pipes?
In Linux, pipes (`|`) are used to pass the output of one command as input to another command. They allow chaining commands together to perform complex tasks without creating intermediate files. For example: `ls -l | grep ".txt"` lists only `.txt` files.

## Modes in vi editor?
In Linux, the **vi editor** has three main modes:

* **Normal/Command mode** – Default mode for navigating, deleting, copying, or saving text.
* **Insert mode** – Used to insert or edit text (entered by pressing `i`, `a`, or `o`).
* **Visual mode** – Used to select text for copying, deleting, or formatting (entered by pressing `v`).

Switching between modes allows efficient text editing.

## How to undo/redo in vim?
In Linux `vim`, we can undo changes by pressing `u` in normal mode. To redo changes that were undone, press `Ctrl + r` in normal mode. This allows you to easily correct mistakes while editing files.

## How to save file in vim/nano?
In Linux:

* In **vim**, press `Esc` to enter normal mode, then type `:w` to save, `:wq` to save and quit, or `:q!` to quit without saving.
* In **nano**, press `Ctrl + O` to write/save the file, then `Enter` to confirm, and `Ctrl + X` to exit.

These commands ensure your changes are stored properly.
