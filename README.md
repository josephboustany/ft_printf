
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
  - `%%` - Percent symbol
- **Flags**: Supports common flags such as:
  - `-` - Left-justify the output within the given field width
  - `0` - Pads with zeros instead of spaces
- **Width and Precision Modifiers**:
  - Width allows specifying the minimum number of characters to output.
  - Precision adjusts the number of characters for strings or the number of digits for numbers.
- **Custom Parsing and Error Handling**: A parser processes the format string to interpret specifiers, flags, width, and precision settings, with custom error handling to manage unsupported format options.

## Code Structure
The project is organized into three primary files:
1. **`ft_printf.c`**:
   - Contains the main `ft_printf` function, which parses the format string and calls helper functions for each specifier.
   - Uses the `process_format_specifier` function to identify and handle each format specifier encountered in the format string.
2. **`ft_printf.h`**:
   - Header file defining function prototypes and necessary includes, such as `<stdarg.h>` for variadic argument handling and `<unistd.h>` for low-level I/O.
3. **`ft_printf_part2.c`**:
   - Includes additional helper functions that handle unsigned integers, hexadecimal numbers, and memory addresses. These functions provide support for `%u`, `%x`, `%X`, and `%p`.

## Functionality and Functions
### Main Functions
- **`ft_printf(const char *str, ...)`**: Main function that iterates through the format string `str`, identifying format specifiers and invoking appropriate handlers. It returns the total character count of the output.
- **`process_format_specifier(char next, va_list args)`**: Handles each format specifier encountered in `ft_printf`:
  - `%c` - Calls `ft_putchar` to print a character.
  - `%s` - Calls `ft_putstr` to print a string.
  - `%d`, `%i` - Calls `ft_putnumbr` for signed integers.
  - `%u` - Calls `ft_putunumbr` for unsigned integers.
  - `%x`, `%X` - Calls `ft_puthexadecimal` with lowercase or uppercase hexadecimal representation.
  - `%p` - Calls `ft_putaddress` to print a pointer address.

### Helper Functions
- **`ft_putchar(int c)`**: Writes a single character `c` to standard output.
- **`ft_putstr(char *s)`**: Writes a null-terminated string `s` to standard output.
- **`ft_putnumbr(int number)`**: Recursively handles and prints signed integers, managing edge cases like `INT_MIN`.
- **`ft_putunumbr(unsigned int number)`**: Recursively handles and prints unsigned integers.
- **`ft_puthexadecimal(unsigned int number, char *base)`**: Recursively prints an unsigned integer in hexadecimal format, using the specified base for uppercase or lowercase representation.
- **`ft_putaddress(void *ptr)`**: Converts a pointer to a hexadecimal string representation, prefixing it with `0x`.

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
ft_printf("Pointer: %p\n", &main);                // Output: Pointer: 0x[address]
ft_printf("Left-justify: %-5d!\n", 42);           // Output: Left-justify: 42   !
ft_printf("Zero-padding: %05d\n", 42);            // Output: Zero-padding: 00042
```

## Learning Objectives
Through this project, the following skills are developed:
- **Variadic Functions**: Usage of `va_list`, `va_start`, `va_arg`, and `va_end` to handle variable arguments.
- **Recursive Printing**: Techniques for recursively handling integer and hexadecimal conversions.
- **Error Handling**: Managing unsupported or incorrect format specifiers.
- **Memory Management**: Efficient handling of buffers to ensure stability and avoid memory leaks.

## License
This project is licensed under the MIT License. Refer to the `LICENSE` file for more details.

## Acknowledgments
This project was developed as part of the 42 School curriculum to gain experience in low-level C programming and understand the mechanisms behind standard library functions.
