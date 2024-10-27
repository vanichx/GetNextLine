**get_next_line**

### Description

The **Get Next Line (GNL)** function is designed to read lines from a file descriptor one at a time without interrupting the reading sequence. This project offers foundational practice with file manipulation and dynamic memory allocation in C, allowing for flexible reading from standard input, files, or even network sockets.

### Features

- Reads a single line from a specified file descriptor
- Supports simultaneous reading from multiple file descriptors
- Works with any buffer size defined by the user
- Can read from standard input, files, or other descriptors

### Usage

To use **Get Next Line** in your project:

1. Clone this repository to your local machine.
2. Include the `get_next_line.h` header file in your project.
3. Use `get_next_line()` in your code, providing a file descriptor and a pointer to a `char*` variable as arguments.
4. Repeat the function call until it returns 0 (end of file), -1 (error), or 1 (line read successfully).

#### Example

A simple usage example in a C file:

```c
int main(void) {
    int fd;
    char *line;

    fd = open("example.txt", O_RDONLY);
    line = get_next_line(fd);
    while (line) {
        printf("%s", line);
        free(line);
        line = get_next_line(fd);
    }
    close(fd);

    return (0);
}
```

### Compilation

- **Without a specified buffer size** (default is set to 42 in the header file):
  ```bash
  cc -Wall -Wextra -Werror get_next_line.c get_next_line_utils.c main.c get_next_line.h
  ```
- **With a specified buffer size**:
  ```bash
  cc get_next_line.c get_next_line_utils.c main.c -D BUFFER_SIZE=<size>
  ```

### Parameters

- `int fd`: File descriptor to read from.
- `char **line`: Pointer to store the line read from the file descriptor.

### Return Values

- **1** if a line has been read.
- **0** if the end of the file is reached.
- **-1** if an error occurred.
