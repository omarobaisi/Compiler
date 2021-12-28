# Made a Lexical analyzer and a parser for a programming language called teenytiny

# project description :-

### Compiler Design Project <br>
For this course, you are required to build a compiler for a toy language called “Teeny Tiny Language”. The project is split into three milestones: lexical analyzer, parser, code generator. You can use any language of your choice (C, Java, Python, etc). Please document your code and follow your programming language’s style guidelines. Using git is very recommended, but not necessary. Points will be deducted for lack of documentation and unclean code. <br>

By documenting your program, I do not mean writing a separate document explaining what your program does. Instead, I mean adding the README.txt file, apply coding conventions, etc. For more information, look up online how to document your code! You can also use documentation tools such as Javadoc or linters to ensure that your code is clean. <br>

After completing each stage/milestone, push your changes to the git repository and upload your code to the e-class. The deadlines for submitting the code for each stage are as follow:<br>

Lexical analyzer	Parser<br>
November 6th	November 27th<br>

After you complete each stage, I will upload a document on the e-class to help you with the next stage. <br>

### Lexical Analyzer

The lexical analyzer or scanner is responsible for reading the source file of the program character by character and grouping them into tokens.
A token is a sequence of characters that represents a unit of information in the source program. Examples of tokens in popular programming languages are keywords such as the word “if” or “int”. Identifiers (user-defined names) and special symbols (+, -) are also tokens. <br>

The job of a scanner is essentially pattern matching/recognition. As such, modeling your program using finite automata might be very helpful!
Given a string in a file, your program will iterate through it character by character and identify tokens. If your program stumbles across an unrecognized token that does not belong to the Teeny Tiny Language, you must report an error for an invalid token. <br>

The Teeny Tiny language you are going to implement will the support numerical variables, basic arithmetic, if-statements, while-loops, printing text and numbers, inputting text, and comments. <br>

Types of tokens your program must recognize are:<br>
•	Numbers: one or more numeric characters followed by an optional decimal point and one or more numeric characters.<br>
•	Identifiers: an alphabetical character followed by zero or more alphanumeric characters.<br>
•	Keywords: exact text match of: PRINT, INPUT, LET, IF, THEN, ENDIF, WHILE, REPEAT, ENDWHILE<br>
•	Operators: + - * / = == != > < >= <=<br>
•	Strings:  double quotation followed by zero or more characters and a double quotation. Such as: "hello, world!" and ""<br>

Your program must skip comments and whitespaces. HINT: use enums to represent tokens. <br>
For each identified token, your program must print the token type. Your program must stop when it consumes all the file or encounters an unrecognizable token. Example output:<br>
Assuming you have a source file that contains the text: IF 200>2 THEN PRINT”yes” and<br>

assuming you named your enum “Token”:<br>

Please enter name of your file: teenytiny.txt<br>
Token.IF<br>
Token.NUMBER<br>
Token.GREATERTHAN<br>
Token.NUMBER<br>
Token.THEN<br>
Token.PRINT<br>
Token.STRING<br>


Prasing grammer :-

program ::= {statement}<br>
statement ::= "PRINT" (expression | string) nl<br>
            | "IF" comparison "THEN" nl {statement} "ENDIF" nl<br>
            | "WHILE" comparison "REPEAT" nl {statement} "ENDWHILE" nl<br>
            | "LABEL" ident nl<br>
            | "GOTO" ident nl<br>
            | "LET" ident "=" expression nl<br>
            | "INPUT" ident nl<br>
comparison ::= expression (("==" | "!=" | ">" | ">=" | "<" | "<=") expression)+<br>
expression ::= term {( "-" | "+" ) term}<br>
term ::= unary {( "/" | "*" ) unary}<br>
unary ::= ["+" | "-"] primary<br>
primary ::= number | ident<br>
nl ::= '\n'+<br>
