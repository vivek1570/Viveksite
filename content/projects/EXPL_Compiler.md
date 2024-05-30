---
title: Toy-Compiler(EXPL)
date: "2024-03-02"
draft: false
hideLastModified: true
toc: true
weight: 10
keepImageRatio: true
tags:
  - Compiler
  - Academic
summary: "A Toy Compiler"
showInMenu: false
---

<a href="https://github.com/vivek1570/EXPL-NITC" target="_blank" style="color: white; background-color: Gray; padding: 5px 5px; text-align: center; text-decoration: none; display: inline-block; border-radius: 20px; font-size:15px">EXPL-NITC</a>

## Compiler Design Project

```
+--------------------+         +--------------------+         +--------------------+
| Source Code (EXPL) |--------->| Lexical Analyzer |--------->| Syntax Analyzer  |
+--------------------+         +--------------------+         +--------------------+
                   |             (Recognizes tokens)               (Checks grammar)
                   v             |                               v
             +---------+          +---------+                         +---------+
             | Scanner |          | Parser  |                         | Symbol Table |
             +---------+          +---------+                         +---------+
                   |             (Builds token stream)               (Builds AST)
                   v             |                               v
             +---------+          +---------+                         +---------+
             | Error   |          | Error   |                         | Semantic Analyzer |
             +---------+          +---------+                         +---------+
                   |             (Reports lexical errors)           (Reports syntax errors)
                   v                                                 v
             +---------+                                             +---------+
             | Output  |                                             | Intermediate |
             +---------+                                             +---------+
                   |             (Intermediate Representation)           | Representation |
                   v                                                 v
             +---------+                                             +---------+
             | (Optional) |                                             | Target Code |
             +---------+                                             +---------+
                   |             (Assembly or Bytecode)               | Generation |
                   v                                                 v
             +---------+                                             +---------+
             | Optimized |                                             | (Optional) |
             +---------+                                             +---------+
                   |             (Improved Intermediate Representation) | Optimization |

```

**Specifications:**

- **Source Language:** Experimental Language (ExpL) - Informal specification [here](https://silcnitc.github.io/expl-docs/).
- **Extension for Object Oriented Programming:** [Specs here](oop_extension_specification_link).
- **Target Platform ABI:** Experimental Operating System (ExpOS) on Experimental String Machine (XSM) - ABI [here](https://silcnitc.github.io/expl-docs/).

**Description:**

Designed and implemented a compiler for ExpL, a language developed for instructional purposes. The project involved:

- Lexical analysis using LEX to identify lexical elements.
- Syntax analysis phase to check for syntax errors.
- Semantic analysis phase to detect type and scope errors.
- Generation of abstract syntax tree representation.
- Front end compilation process from lexical analysis to abstract syntax tree generation.

This project required systematic mapping of source language constructs to semantically equivalent constructs in the target language, while preserving program semantics.

![expl](https://silcnitc.github.io/expl-docs/img/flowdiagram.png)

**Main Achievements:**

- Successfully implemented lexical analysis, syntax analysis, and semantic analysis phases.
- Developed an intermediate representation of source programs in the form of abstract syntax trees.
- Ensured preservation of program semantics throughout the translation process.

<a href="https://github.com/vivek1570/EXPL-NITC" target="_blank" style="color: white; background-color: Gray; padding: 10px 20px; text-align: center; text-decoration: none; display: inline-block; border-radius: 20px;">EXPL-NITC</a>
