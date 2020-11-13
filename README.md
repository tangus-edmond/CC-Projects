# CC-Projects
Assignments and Labs from the Compiler Construction course.

## Project Team
  * 100189

### Lab 1 - Lexical Analyzer
1) A simple lexical analyzer implementation in C++
2) An automatic lexical analyzer implementation using Flex (Bonus)

#### Running the Lexical Analyzer using Lex (2)
A scanner that recognizes integers, four basic arithmetic operators and a unary absolute value operator.

Requirements:
1) Ubuntu/Linux OS
2) Install flex - `sudo apt install flex`

Once flex is installed we can now run "analyzer.l" <br>
  ```
  $ flex analyzer.l
  $ cc lex.yy.c -lfl
  $ ./a.out
  ["User Input e.g 24 + 37"]
  $ CTRL + D (to exit the program)
  ```

### Lab 2- Describing the Outputs (Lab 1)

