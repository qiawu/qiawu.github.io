---
title: How a compiler works
date: 2017-02-01 20:30:43
tags:
- 技术
- Compiler
---
## Core Components:
1. Lexical Analyzer
2. AST Parser
3. Interpreter (use visitor pattern to traverse the AST)
4. Symbol table
<!--more-->

![](/images/Compiler1.png)

## AST
### context-free grammers
example:
Parsing 
7 + 3 * (10 / (12 / (3 + 1) - 1)) 
![](/images/Compiler2.png)
![](/images/Compiler3.png)
![](/images/Compiler4.png)

### context-free grammers to AST:
![](/images/Compiler5.png)

### parsing a programe:
![](/images/Compiler6.png)
![](/images/Compiler7.png)
