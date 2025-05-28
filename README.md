# Experiment No: 13A – Stack Implementation using List

## AIM:
To write a Python program to implement a stack using list and its built-in methods `append()` and `pop()`.

---

## ALGORITHM:
1. Define a class named `st` to represent the stack.
2. Inside the class:
   - Define the method `push(L)` to append even numbers from 1 to L into the stack.
   - Define the method `pop()` to remove the top element from the stack and display it.
   - Define the method `peek()` to display current elements of the stack.
3. Create an instance of the class.
4. Get input value `L` from the user.
5. Call `push(L)` to populate the stack with even numbers up to `L`.
6. Call `peek()` to show the stack elements.
7. Call `pop()` to remove the top element.
8. Call `peek()` again to display updated stack.

---

## PROGRAM:
```python
stack = []
class st:
    def push(self, L):
        for i in range(1, L):
            if i % 2 == 0:
                stack.append(i)
    def pop(self):
        print(f"Element popped :  {stack.pop()}")
    def peek(self):
        print(f"Elements in the stack \n {stack}")

L = int(input())
no = st()
no.push(L)
no.peek()
no.pop()
no.peek()
```

## OUTPUT
![image](https://github.com/user-attachments/assets/058cc6dd-919e-4964-ba40-185dc8c9aa61)

RESULT:
Thus, the Python program to implement a stack using a list and built-in methods was successfully executed.



# Experiment No: 13b – Infix to Postfix Conversion

## AIM:
To write a Python program to convert a given infix expression to postfix expression using dictionary for precedence and set for operators.

---

## ALGORITHM:
1. Define a set `op` to include valid operators: `|`, `%`, `*`, `(`, `)`.
2. Define a dictionary `pri` to set the precedence for operators.
3. Create a function `in_to_post(exp)` to convert infix to postfix.
4. Traverse each character in the input expression:
   - If the character is an operand, append to output.
   - If it is `'('`, push to stack.
   - If it is `')'`, pop from stack to output until `'('` is encountered.
   - If it is an operator, pop from stack to output based on precedence, then push the current operator.
5. After traversal, pop any remaining operators in the stack to the output.

---

## PROGRAM:
```python
op = set(['|', '%', '*', '(', ')'])
pri = {'|': 1, '%': 2, '*': 2}

def in_to_post(exp):
    stack = []
    out = ''
    for char in exp:
        if char not in op:
            out += char
        elif char == '(':
            stack.append('(')
        elif char == ')':
            while stack and stack[-1] != '(':
                out += stack.pop()
            stack.pop()
        else:
            while stack and stack[-1] != '(' and pri[char] <= pri[stack[-1]]:
                out += stack.pop()
            stack.append(char)
    while stack:
        out += stack.pop()
    return out

exp = input()
print(f"infix notation:  {exp}")
print(f"postfix notation:  {in_to_post(exp)}")
```

### OUTPUT
![image](https://github.com/user-attachments/assets/989ee50f-4280-41d6-a624-a1300353bac2)


### RESULT
Thus, the Python program to convert infix expression to postfix expression was successfully executed following precedence and associativity rules.


# Experiment No: 13c – Tower of Hanoi using Recursion

## AIM:
To write a Python program to solve the Tower of Hanoi problem and display all moves using recursive function.

---

## ALGORITHM:
1. Define a recursive function `TowerOfHanoi(n, source, destination, auxiliary)`.
2. If `n > 0`, perform the following steps:
   - Move `n-1` disks from `source` to `auxiliary` using `destination` as auxiliary.
   - Print move from `source` to `destination` for the nth disk.
   - Move `n-1` disks from `auxiliary` to `destination` using `source` as auxiliary.

---

## PROGRAM:
```python
def TowerOfHanoi(n, source, destination, auxiliary):
    if n > 0:
        TowerOfHanoi(n-1, source, auxiliary, destination)
        print(f"Move disk from {source} to {destination}")
        TowerOfHanoi(n-1, auxiliary, destination, source)

n = int(input())
print("No. of disks =", n)
TowerOfHanoi(n, 'A', 'C', 'B')
```

### OUTPUT
![image](https://github.com/user-attachments/assets/6fa28395-3ee8-4808-9eae-b035a787176d)


### RESULT
Thus, the Python program to solve the Tower of Hanoi problem using recursion was successfully executed and displayed the correct disk moves.


# Experiment No: 13d – Evaluation of Postfix Expression using Stack

## AIM:
To write a Python program to evaluate a given postfix expression that contains Multiplication and Addition operators using stack.

---

## ALGORITHM:
1. Define a set of operators.
2. Traverse the postfix expression.
3. If the character is an operand, push it to the stack.
4. If it is an operator, pop two operands from the stack, evaluate the result, and push it back.
5. Return the final value from the stack.

---

## PROGRAM:
```python
OPERATORS = set(['*', '-', '+', '%', '/', '**'])

def evaluate_postfix(expression):
    stack = []
    for i in expression:
        if i not in OPERATORS:
            stack.append(i)
        else:
            a = stack.pop()
            b = stack.pop()
            if i == '+':
                res = int(b) + int(a)
            elif i == '-':
                res = int(b) - int(a)
            elif i == '*':
                res = int(b) * int(a)
            elif i == '%':
                res = int(b) % int(a)
            elif i == '/':
                res = int(b) / int(a)
            elif i == '**':
                res = int(b) ** int(a)
            stack.append(res)
    return stack[0]

expression = input()
print('postfix expression: ', expression)
print('Evaluation result: ', evaluate_postfix(expression))

```


### OUTPUT
![image](https://github.com/user-attachments/assets/94f6a562-e75b-4768-b886-42f0982f44f9)

### RESULT
Thus, the Python program for evaluating a postfix expression using stack was successfully executed and the output was verified.


# Experiment No: 13e – Evaluation of Prefix Expression using Stack

## AIM:
To write a Python program to evaluate a user-given prefix expression using stack.

---

## ALGORITHM:
1. Define a set of valid operators.
2. Traverse the prefix expression in reverse.
3. If a character is an operand, push it to the stack.
4. If it's an operator, pop two operands, evaluate, and push the result.
5. Return the final result from the stack.

---

## PROGRAM:
```python
op = set(['*', '-', '+', '%', '/', '**'])

def evaluate(exp):
    stack = []
    for c in exp[::-1]:
        if c not in op:
            stack.append(int(c))
        else:
            o1 = stack.pop()
            o2 = stack.pop()
            if c == '+':
                stack.append(o1 + o2)
            if c == '-':
                stack.append(o1 - o2)
            if c == '%':
                stack.append(o1 % o2)
            if c == '/':
                stack.append(o1 / o2)
            if c == '*':
                stack.append(o1 * o2)
            if c == '**':
                stack.append(o1 ** o2)
    return stack.pop()

test = input()
print("Prefix Expression :", test)
print("Evaluation result :", evaluate(test))

```

### OUTPUT
![image](https://github.com/user-attachments/assets/268978cf-e188-41c0-92cc-1e7d09e7aef3)

### RESULT
Thus, the Python program to evaluate a prefix expression using stack was executed successfully and verified.


