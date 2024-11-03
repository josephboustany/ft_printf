
# ft_printf

## Project Overview
`ft_printf` is a custom implementation of the C standard `printf` function, developed as part of the 42 School curriculum. This project was designed to deepen understanding of variadic functions, string formatting, memory management, and low-level C programming concepts. Re-implementing `printf` from scratch provides valuable insight into how formatted output is managed without relying on the C Standard Library.

## Features
This `ft_printf` project includes the following key features:
- **Format Specifiers**: Supports multiple format specifiers, including:
  - `%c` - Single character
  - `%s` - String
  - `%d` and `%i` - Signed integers
  - `%u` - Unsigned integer
  - `%x` and `%X` - Hexadecimal (lowercase and uppercase)
  - `%p` - Pointer address
- **Flags**: Supports common flags such as:
  - `-` - Left-justify the output within the given field width
  - `0` - Pads with zeros instead of spaces
- **Width and Precision Modifiers**:
  - Width allows specifying the minimum number of characters to output.
  - Precision adjusts the number of characters for strings or the number of digits for numbers.
- **Custom Parsing and Error Handling**: A parser processes the format string to interpret specifiers, flags, width, and precision settings, with custom error handling to manage unsupported format options.

## Code Structure
The code is organized into several files, each handling different responsibilities:
- **`ft_printf.c`**: The main function that interprets the format string and calls helper functions based on the format specifiers.
- **`parsing.c`**: Handles parsing of format specifiers, flags, width, and precision modifiers, validating input to ensure correct formatting.
- **`specifier_functions.c`**: Contains helper functions for processing specific format specifiers, such as characters, strings, integers, unsigned integers, and hexadecimal conversions.
- **`utility.c`**: Includes helper functions for memory management, buffer handling, and string manipulation.

## Installation
To use `ft_printf` in your own project:
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ft_printf.git
   ```
2. Compile the code using `make`:
   ```bash
   cd ft_printf
   make
   ```
3. Include `ft_printf.h` in your C files and link the compiled object files during compilation.

## Usage
Once compiled, you can use `ft_printf` just like the standard `printf` function to output formatted text. Here’s an example:

```c
#include "ft_printf.h"

int main() {
    ft_printf("Hello, %s! The answer is %d.\n", "world", 42);
    ft_printf("Character: %c, Hexadecimal: %x\n", 'A', 255);
    return 0;
}
```

## Examples
Here are some examples demonstrating the format specifiers, flags, width, and precision options supported by `ft_printf`:

```c
ft_printf("Character: %c\n", 'A');                // Output: Character: A
ft_printf("String: %s\n", "Hello");               // Output: String: Hello
ft_printf("Integer: %d\n", 123);                  // Output: Integer: 123
ft_printf("Unsigned: %u\n", 456);                 // Output: Unsigned: 456
ft_printf("Hex (lowercase): %x\n", 255);          // Output: Hex (lowercase): ff
ft_printf("Hex (uppercase): %X\n", 255);          // Output: Hex (uppercase): FF
ft_printf("Pointer: %p\n", &variable);            // Output: Pointer: 0x7ffeedcba987
ft_printf("Formatted number: %05d\n", 42);        // Output: Formatted number: 00042
ft_printf("Left-justified: %-5d\n", 42);          // Output: Left-justified: 42   
ft_printf("Precision: %.2f\n", 3.14159);          // Output: Precision: 3.14
```

## Learning Objectives
This project focuses on developing the following skills:
- **Variadic Functions**: Using `va_list`, `va_start`, `va_arg`, and `va_end` to process a variable number of arguments.
- **Memory Management**: Efficient handling of buffers to avoid memory leaks and ensure smooth performance.
- **Error Handling**: Managing unsupported or incorrect format specifiers and handling edge cases.
- **Modular Code Structure**: Organizing the project to separate parsing, formatting, and output functions, enhancing readability and maintainability.

## License
This project is open-source and available under the MIT License. See the `LICENSE` file for more details.

## Acknowledgments
This project was developed as part of the 42 School curriculum to gain practical programming experience in C and understand the inner workings of commonly used functions.
