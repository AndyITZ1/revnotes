# Java
-  general purpose computer-programming language that is **concurrent, class-based, object-oriented, and specifically designed to have as few implementation dependenices as possible** 
- intended to let app developers **"write once, run anywhere"** (WORA)
    - compiled Java code can run on all platforms that support Java without needing to recompile the code
- Java applications are typically compiled to bytecode that can run on any Java virtual machine (JVM) regardless of the computer architecture

## Conditional Statements
- Java has 4 different types of **decision making statements/structures**:
    - IF statements
    - IF..ELSE statements
    - NESTED IF statements
    - SWITCH statements
- All of these decision making structures, evaluate one or more conditions to run one or more statements based on conditions being met or not met.
    - If condition true then run some statements, if false run other statements

### IF Statements
#### Syntax
```Java
if (condition) {
    // Statement 1
    // Statement 2
    // Statement N
}
// Following code
```
- With IF statements, when the condition evaluates to true all statements enclosed in the curly brackets are executed as part of the code.
- If the condition is false, then immediately the code after the IF statement (after the ending curly bracket) will begin executing and anything in the IF block is not executed

### IF..ELSE Statements
#### Syntax
```Java
if (condition) {
    // Statement 1
    // Statement 2
    // Statement N
}
else {
    // Statement 1
    // Statement 2
    // Statement N
}
// Following code
```
- Similar to IF statements, when the condition is true the statements in the IF block are executed, otherwise if the condition is false the statements in the ELSE block are ran.
- And after either execution of block statements the program will resume with the code following the ending curly bracket for the ELSE statement
- Note that the ELSE statement is rather optional and not necessary unless a developer intends to run a set of statements when the condition evaluates to false

### IF..ELSE IF Statement
#### Syntax
```Java
if (condition) {
    // Statement 1
    // Statement 2
    // Statement N
}
else if (condition2) {
    // Statement 1
    // Statement 2
    // Statement N
}
else {

}
// Following code
```
- Similar to how IF..ELSE statements work, there's a new statement ELSE IF, which has its own block and has its own condition.
- The ELSE IF block is reached if the previous condition evaluated before it is false (just like an ELSE statement with a condition now)
- Upon the ELSE IF block being reached then it condition evaluates if true then just like an IF statement it will execute everything in its block, otherwise if false then it will move to the next block
- You can chain multiple ELSE IF statements one after another (unlike where you only have one IF statement and one ELSE statement)
- ELSE IF statements never start as the initial statement as the IF statement is always the start, but however it can be ending/last block to be evaluated as the ELSE block is optional 

## NESTED IF Statements
- refers to when there is an IF statement inside another IF statements block
```Java
if (condition) {
    if (condition2) {
        // Some statements
    }
    // Some statements
}
```
- Note that IF statements can be inside/nested in any block (IF, ELSE IF, ELSE)

## SWITCH Statement
- Instead of a condition being evaluated, a **variable's value** is used to test equality against a list of **cases** (values) that will execute statements if the variable value matches one of the cases
### Syntax
```Java
switch(variable) {
    case value1 :
        // Statements
        break; // optional
    case valueN :
        // Statements
        break; // optional
    default : // optional
        // Statements
}
```
- Similar to IF..ELSE Statements, the last block (ELSE statement) is optional but used when all the conditions/cases are evaluated to false. For a switch statement, the **default** case is the equivalent **ELSE** statement.
- You can have any number of cases and these are like IF statement (first **case**) and the multiple ELSE IF statements you can have.

## SWITCH Statement Rules
- The variable that is used has to either an integer, convertable integer type(byte, short, char), strings or an enum data type
- Each case is followed by a value that is used to match the variable to execute that case and the syntax shows that you have a colon following that value to start that block
- When the variable matches a case then all statements following that case are executed until a **break statement** is reached.
- This also means that break statements are optional, but are helpful if you need to end so that the only statements executed are the ones starting from the case that was matched to the end where the break statement is located.
- No break statement is needed for the default case as its always the last to execute.
