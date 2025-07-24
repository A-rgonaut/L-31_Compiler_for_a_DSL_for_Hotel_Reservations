# Compiler for a DSL for Hotel Reservations

![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white)

> Team implementation of a C compiler, using Flex and Bison tools, for hotel room reservations.
## 📖 **Context**

This project was developed for the **Compilatori** examination of Prof. **Sabrina Mantaci**, during the **2022/2023** Academic Year at the **Università degli Studi di Palermo**, **Computer Science (L-31, 2086)** course.

## 👥 **Authors**
_Andrea Spinelli - Marco Valenti_

## 🛠️ **Technologies Used**

*   **Languages:** C
*   **Other:** Git

## 🚀 **Installation and Startup**

To compile and run this project, you will need a C compiler and the standard compiler-construction tools.

### Prerequisites

*   A C compiler (e.g., **GCC**)
*   **Flex** (Lexical Analyzer Generator)
*   **Bison** (Parser Generator)
*   **`make`** (Build Automation Tool)

> **Note**: On Linux (like Ubuntu/Debian), you can install these tools with: `sudo apt-get install build-essential flex bison`.
> On macOS, these are included with the Xcode Command Line Tools.
> On Windows, you can use a toolchain like [MinGW-w64](https://www.mingw-w64.org/) and install Flex/Bison for Windows.

### Instructions

1.  **Clone the Repository**
    Open your terminal and clone the repository to your local machine.
    ```bash
    git clone https://github.com/A-rgonaut/L-31_Compiler_for_a_DSL_for_Hotel_Reservations.git
    cd L-31_Compiler_for_a_DSL_for_Hotel_Reservations
    ```

2.  **Compile the Project**
    Use the provided `Makefile` to build the compiler. This will generate the parser/scanner C files and compile all sources into a single executable.
    ```bash
    make
    ```
    This will create an executable file named `HotelBookingCompiler` in the root directory.

3.  **Run the Compiler**
    The compiler takes one argument: the path to a source file written in the hotel booking DSL. You can use the provided test files to see it in action.
    ```bash
    # Run with the first test file
    ./HotelBookingCompiler test.txt

    # Run with the second test file
    ./HotelBookingCompiler test2.txt
    ```

4.  **How to Write Source Files**
    You can create your own `.txt` files with commands for the compiler to execute. For example:
    ```
    # file: my_commands.txt

    LIST_ROOMS_AVAILABILITY 2024-12-25

    BOOK_ROOM 101 2024-12-24 2024-12-26 "Alice Smith"
    
    SHOW_RESERVATIONS
    ```
    And then run it with: `./HotelBookingCompiler my_commands.txt`

5.  **Clean Up**
    To remove the generated object files and the final executable, you can use the `clean` command from the `Makefile`.
    ```bash
    make clean
    ```

## ✨ **Key Features**

This project is the implementation of a compiler for a custom **Domain-Specific Language (DSL)** designed for managing hotel room reservations. The compiler is built in C using the standard compiler-construction tools, **Flex** and **Bison**.

The core features are:

1.  **Custom Domain-Specific Language (DSL)**: The project defines a simple, readable language for performing hotel management tasks. Based on your test files, the supported commands include:
    *   `LIST_ROOMS_AVAILABILITY <date>`: Checks which rooms are free on a specific date.
    *   `BOOK_ROOM <room_number> <start_date> <end_date> "<guest_name>"`: Creates a new reservation for a room.
    *   `CANCEL_RESERVATION <reservation_id>`: Cancels an existing reservation.
    *   `SHOW_RESERVATIONS`: Lists all current reservations.

2.  **Classic Compiler Architecture**: The compiler is built using a standard and robust toolchain:
    *   **Flex (Lexical Analysis)**: The `scanner.l` file defines the tokens of the language (keywords like `BOOK_ROOM`, numbers, strings, dates).
    *   **Bison (Syntactic Analysis)**: The `parser.y` file defines the grammar of the DSL, ensuring that sequences of tokens form valid commands.

3.  **Abstract Syntax Tree (AST)**: The compiler parses the source code and builds an Abstract Syntax Tree (as defined in `include/ast.h`). This tree is a structured, in-memory representation of the commands, which is a key component of a well-designed compiler.

4.  **Symbol Table Management**: The project uses a Symbol Table (`include/stable.h`) to keep track of the state of the hotel, such as active reservations, associating reservation IDs with guest details and dates.

5.  **Direct Execution**: The compiler interprets the AST and directly executes the commands, printing the results to the standard output (e.g., confirming a booking or listing available rooms).
