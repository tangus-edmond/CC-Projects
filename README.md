# CC-Projects
Assignments and Labs from the Compiler Construction course.

## Contents
  - Lab 1 - Lexical Analyzer
  - Lab 2- Describing the Outputs

## Lab 1 - Lexical Analyzer
1) A simple lexical analyzer implementation in C++
2) An automatic lexical analyzer implementation using Flex (Bonus)

### Running the Lexical Analyzer using Lex (2)
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

## Lab 2- Describing the Outputs

We shall use the Lab 1 (2. Lexical Analyzer using Lex) lexer `analyzer.l`.

A snippet of the output after running:
```
13 + 25
NUMBER 13
PLUS
NUMBER 25
NEWLINE
57 / q
NUMBER 57
DIVIDE
Error! Input q is not an integer
NEWLINE
```
__The output explained:__

The scanner has identified tokens based on the regex rules defined in `analyzer.l`. There are nine patterns defined in the scanner:

The first five patterns are literal operators, written as quoted strings, and their actions, they print a message saying what matched. The sixth pattern matches an integer. <br/>
```
"+" { printf("PLUS\n"); }
"-" { printf("MINUS\n"); }
"*" { printf("TIMES\n"); }
"/" { printf("DIVIDE\n"); }
"|" { printf("ABS\n"); }
```

The bracketed pattern [0-9]matches any single digit, and + sign  matches a string of one or more digits. The action prints out the string that’s matched, using the pointer `yytext` that the scanner sets after each match. <br/>

`[0-9]+ { printf("NUMBER %s\n", yytext); }` <br/>

The seventh pattern matches a newline character, represented by the C `\n` sequence. <br/>

`\n { printf("NEWLINE\n"); }` <br/>

The eighth pattern ignores whitespace. It matches any single space or tab `\t`, and the empty action code does nothing. <br/>

`[ \t] { }` <br/>

The final pattern is the catchall to match anything the other patterns didn’t. Its action code prints an error. <br/>

`. { printf("Error! Input %s is not an integer \n", yytext); }`
