---
layout: page
title: SNUPL/2 Compiler
description: A complete x86-64 compiler written from scratch in C
importance: 2
category: systems
---

**September 2023 – December 2023**

A full compiler for SNUPL/2, a small imperative language, built end to end in **C** with no compiler-construction libraries — no lex, no yacc, no LLVM.

The pipeline is the whole thing:

- **Lexical analysis** — hand-written scanner producing the token stream
- **Parsing** — recursive descent over the SNUPL/2 grammar
- **AST construction** — a typed intermediate representation of the program
- **Semantic analysis** — scope and symbol-table management, type checking
- **Code generation** — emitting **x86-64 assembly** directly, including register allocation and stack frame layout by hand

Writing the backend was the part that changed how I read code. Deciding which values live in registers and which spill to the stack makes the cost of an abstraction concrete in a way that reading about it does not — and it is the same instinct I now apply to where a packet should be processed.

*The source repository is kept private, since SNUPL/2 is a course assignment and publishing solutions would undercut the course.*
