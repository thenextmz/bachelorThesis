# A Tool for Verifying Programs using Constraint Horn Clauses

This is a tool for program verification that uses the theories of 
Constraint Horn Clauses and an algorithm based on the weakest 
liberal precondition algorithm seen in the paper [Horn Clause Solvers for Program Verification](https://link.springer.com/chapter/10.1007/978-3-319-23534-9_2)
by Nikolaj Bjørner et al..

## Installation

Install [Java](https://www.java.com/de/download/manual.jsp)
```bash
sudo apt-get update
sudo apt-get install default-jdk
```
Install [Python3](https://www.python.org/download/releases/3.0/)
```bash
sudo apt-get install python3 
```

Install [Scala 2.11.12](https://scala-lang.org/download/2.11.12.html)
```bash
sudo apt-get install scala
```

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install [Z3](https://github.com/Z3Prover/z3).

```bash
sudo apt install python3-pip
pip install z3-solver
```

## Usage
Inside the src folder where the tool.scala file lies run:
```bash
scala -nc tool.scala ../FILEPATH/inputFile.txt [-bv BitVectorSize]
```
The optional parameter -bv determines if bitvector 
arithmetic is to be used instead of integer arithmetic 
and the BitVectorSize determines its size. 
The BitVectorSize argument is mandatory if the -bv flag is used.

## No operator precedence!
When writing programs note that there is no no operator precedence. 
In this case this can be achieved by using parentheses in the right way. 
See the following examples for more explanation. 
```bash
x := 1 + 2 / 3 + 4 =>      Wrong Evaluation
x := 1 + 2 / (3 + 4) =>    Wrong Evaluation
x := (1 + 2) / (3 + 4) =>  Right Evaluation

x := (1 + 2) / (3 + 4) / (4 + 5) =>    Wrong Evaluation
x := ((1 + 2) / (3 + 4)) / (4 + 5) =>  Right Evaluation
```