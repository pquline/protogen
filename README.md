# PROTOGEN

[`protogen`](./protogen) is a Bash script designed to automate the process of extracting and organizing function prototypes from C source files. This script scans through your project's directory structure, identifies all `.c` files, and extracts their function prototypes, excluding `static` functions and `main`. It then formats and prints them, grouped by subdirectory and sorted by return type and function name.

## Table of Contents

- [Features](#features)
- [Example Output](#example-output)
- [Usage](#usage)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Script Breakdown](#script-breakdown)
- [Customization](#customization)
- [Contributing](#contributing)

## Features

- **Automated Function Prototype Extraction**: Scans through subdirectories to extract non-static function prototypes.
- **Formatted Output**: Outputs neatly formatted prototypes, grouped by subdirectory, and sorted by return type and function name.
- **Customizable Section Headers**: Generates customizable comment headers for each subdirectory section.

## Example Output

Here's an example of what the output might look like when you run the script:

```c
/* --------------------------------- FOLDER1 -------------------------------- */

char	function2(char c);

t_var	*function4(void *content);

void	function1(t_var *var);
void	function3(t_var *var);

/* --------------------------------- FOLDER2 -------------------------------- */

int	function6(int a, int b);

void	function5(char **argv);
void	function7(char *string);
```

This output can be directly included in your header file.

## Usage

1. **Copy the Script**: Copy the `Function Prototype Extractor` script to the root directory of your C project or any location you prefer.

2. **Run the Script**:
    ```bash
    ./protogen
    ```
    This will generate and print the function prototypes grouped by subdirectory.

3. **Include the Output**: You can redirect the output to a file or copy and paste it as needed.

### Optional: Create an Alias

To make the script easier to run from any directory, you can add an alias to your shell configuration file (e.g., `.bashrc`, `.zshrc`):

1. **Move the Script**: Place the script in a directory of your choice, for example, `~/scripts/`.

2. **Edit Your Configuration File**:
    ```bash
    vim ~/.zshrc  # or ~/.bashrc
    ```

3. **Add an Alias**:
    ```bash
    alias protogen="bash ~/scripts/protogen"
    ```

4. **Reload Your Configuration**:
    ```bash
    source ~/.zshrc  # or ~/.bashrc
    ```

Now, you can simply run `protogen` from any project directory to generate your function prototype list.

## Installation

No installation is required. Simply copy the script into your project directory or create an alias for easy access.

## Project Structure

This script expects your project structure to look something like this:

```txt
project-root/
│
├── srcs/
│ ├── folder1/
│ │ ├── file1.c
│ │ └── file2.c
│ └── folder2/
│   ├── file3.c
│   └── file4.c
```

The script will detect folder1 and folder2 and generate function prototypes for all .c files found within.

## Script Breakdown

Here's a breakdown of what the script does:

- Define Source Directory: The script starts by defining the base directory (BASE_DIR) where all the C source files are located.
- Section Headers: For each subdirectory, the script generates a comment header based on the directory name, formatted as a section separator.
- Function Extraction: The script finds all .c files in each subdirectory, extracts non-static function prototypes, and filters out the main function.
- Sorted Output: The extracted prototypes are sorted by return type and function name, and then printed, grouped by subdirectory.

## Customization

### Change the Base Directory

If your source files are located in a different directory, you can modify the BASE_DIR variable at the beginning of the script:

```bash
BASE_DIR="your_source_directory"
```

### Modify Header Width

If you need to change the width of the generated section headers, adjust the total_length variable inside the print_separator function:

```bash
total_length=100  # or any other width
```

## Contributing

Contributions are welcome! If you have ideas for new features, find a bug, or want to improve the script, feel free to open an issue or submit a pull request.
How to Contribute

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes and commit them.
4. Push your changes to your fork.
5. Submit a pull request.
