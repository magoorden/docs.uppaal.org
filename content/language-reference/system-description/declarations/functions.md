---
title: Functions
weight: 20
---

Functions can be declared alongside other declarations. The syntax for functions is defined by the grammar for `Function`:

```EBNF
Function        ::= [Type] [ID] '(' [Parameters] ')' Block
Block           ::= '{' LocalDeclaration* Statement* '}'
LocalDeclation  ::= TypeDeclaration | VariableDeclaration
Statement       ::= Block
                 | ';'
                 |  [Expression] ';'
                 |  ForLoop
                 |  Iteration
                 |  WhileLoop
                 |  DoWhileLoop
                 |  IfStatement
                 |  ReturnStatement

ForLoop	        ::= 'for' '(' [Expression] ';' [Expression] ';' [Expression] ')' Statement
Iteration       ::= 'for' '(' [ID] ':' [Type] ')' Statement
WhileLoop       ::= 'while' '(' [Expression] ')' Statement
DoWhile         ::= 'do' Statement 'while' '(' [Expression] ')' ';'
IfStatment      ::= 'if' '(' [Expression] ')' Statement [ 'else' Statement ]
ReturnStatement ::= 'return' [ [Expression] ] ';'
```

See [rail road diagram for the entire Function declaration](/grammar/#FunctionDecl).

## Functions

The declarations inside functions include only variable and type declarations. Nested function declarations and recursion are not supported.

## Iteration

The keyword `for` has two uses: the first is a C/C++/Java like for-loop, and the second is a Java like iterator or ranged-loop in C++. The second is primarily used to iterate over arrays indexed by scalars.

A statement `for (ID : Type) Statement` will execute `Statement` once for each value `ID` of the domain of type `Type`. The scope of `ID` is bound to the `Statement`, and `Type` must be a bounded integer or a scalar set.

See also rail road diagrams for the entire [ForStatement](/grammar/#ForStatementt) and [WhileStatement](/grammar/#WhileStatement).


## Examples

### add

The following function returns the sum of two integers. The arguments are call by value.

```c
int add(int a, int b)
{
    return a + b;
}
```

### swap

The following procedure swaps the values of two call-by-reference integer parameters.

```c
void swap(int &a, int &b)
{
    int c = a;
    a = b;
    b = c;
}
```

### initialize

The following procedure initializes an array such that each element contains its index in the array. Notice that the an array parameter is a call-by-value parameter unless an ampersand is used in the declaration. This is different from C++ syntax, where the parameter could be considered an array of references to integer.

```
void initialize(int& a[10])
{
    for (i : int[0,9])
    {
        a[i] = i;
    }
}
```
