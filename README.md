# Made a Lexical analyzer and a parser for a programming language called teenytiny

Using the following grammer

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
