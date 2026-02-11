# Infix to Postfix Converter and Evaluator

This program converts an infix expression to postfix notation and then evaluates the postfix expression to compute the final result using stack data structures.

## Data Structures

The program uses two separate stacks implemented as arrays:

- **opStack[MAX]**: A character array of size 100 that stores operators and parentheses during the infix to postfix conversion process.
- **topOp**: An integer variable tracking the top of the operator stack, initialized to -1 (empty stack).
- **valStack[MAX]**: An integer array of size 100 that stores operand values during postfix expression evaluation.
- **topVal**: An integer variable tracking the top of the value stack, initialized to -1 (empty stack).
- **MAX**: A constant defined as 100, representing the maximum capacity of both stacks.

Both stacks follow the Last-In-First-Out (LIFO) principle. The operator stack is used during conversion, while the value stack is used during evaluation.

## Functions Implemented

### 1. `void pushOp(char x)`
**Purpose**: Pushes an operator or parenthesis onto the operator stack.

This function checks if the operator stack has available space. If not full, it increments the topOp pointer and stores the character at that position. This is used during infix to postfix conversion to temporarily hold operators.

### 2. `char popOp()`
**Purpose**: Removes and returns the operator at the top of the operator stack.

This function checks if the operator stack is empty. If not, it returns the character at the current top position and decrements topOp. If empty, it returns the null character '\0'.

### 3. `void pushVal(int x)`
**Purpose**: Pushes an integer value onto the value stack.

This function checks if the value stack has space available. If not full, it increments topVal and stores the integer at that position. This is used during postfix evaluation to store intermediate calculation results.

### 4. `int popVal()`
**Purpose**: Removes and returns the value at the top of the value stack.

This function checks if the value stack is empty. If not, it returns the integer at the current top and decrements topVal. If empty, it returns 0.

### 5. `int priority(char x)`
**Purpose**: Returns the precedence level of an operator.

This function assigns priority values to operators to determine the order of operations. Addition and subtraction have priority 1, multiplication and division have priority 2, and exponentiation has priority 3. Other characters return 0. Higher priority operators are evaluated before lower priority ones.

### 6. `void convert(char infix[], char postfix[])`
**Purpose**: Converts an infix expression to postfix notation.

This is the core conversion function that processes the infix expression character by character. When a digit is encountered, it's directly added to the postfix expression. Opening parentheses are pushed onto the operator stack. Closing parentheses trigger popping of operators until the matching opening parenthesis is found. For operators, the function pops operators from the stack with equal or higher precedence before pushing the current operator. After processing all characters, remaining operators on the stack are popped and added to the postfix expression.

### 7. `int evaluatePostfix(char postfix[])`
**Purpose**: Evaluates a postfix expression and returns the computed result.

This function processes the postfix expression character by character. When a digit is encountered, it's converted from character to integer and pushed onto the value stack. When an operator is encountered, two operands are popped from the value stack, the operation is performed, and the result is pushed back. The function uses a switch statement to handle different operators including addition, subtraction, multiplication, division, and exponentiation. The final result remaining on the stack is returned.

## Organization of main() Method

The main function follows this sequence:

1. **Variable Declaration**: Two character arrays, `infix` and `postfix`, are declared to store the input expression and converted expression respectively.

2. **Input Collection**: The program prompts the user to enter an infix expression and reads it using `scanf()`.

3. **Conversion**: The `convert()` function is called to transform the infix expression into postfix notation. The result is stored in the postfix array.

4. **Display Postfix**: The postfix expression is printed to show the converted form.

5. **Evaluation**: The `evaluatePostfix()` function is called to compute the final result of the postfix expression, and the result is displayed.

6. **Program Termination**: Returns 0 to indicate successful execution.

## Sample Output

### Run 1: Simple Expression
```
Enter infix expression: 3+5*2
Postfix expression: 352*+
Evaluated result: 13
```

### Run 2: Expression with Parentheses
```
Enter infix expression: (3+5)*2
Postfix expression: 35+2*
Evaluated result: 16
```

### Run 3: Complex Expression
```
Enter infix expression: 2^3+4*5
Postfix expression: 23^45*+
Evaluated result: 28
```

### Run 4: Nested Parentheses
```
Enter infix expression: ((2+3)*4)-5
Postfix expression: 23+4*5-
Evaluated result: 15
```

### Run 5: Division and Subtraction
```
Enter infix expression: 8/2-1
Postfix expression: 82/1-
Evaluated result: 3
```
