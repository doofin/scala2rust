# scala2rust: scala to rust compiler/transpiler
This is a prototype compiler that translates Scala code to Rust code. It is implemented in Scala and uses the Scala compiler to parse the Scala code and generate an abstract syntax tree (AST), which is then translated to Rust code.


## Motivation
Rust is a modern systems programming language that is designed for safety and performance, with a focus on memory safety and zero-cost abstractions, and it is widely used in the industry. However, Rust's syntax can be complex, verbose and confusing, since it mixes archaic C++ syntax with modern functional programming concepts. 


I have written an article to critize Rust's syntax, which can be summarized as:
 - The semicolon at the end of the statement is completely unnecessary
 - Each case of match requires curly braces or commas for multi-line statements. This can be handled by the syntax parser
 - let mut x=a is not as good as let x=mut a
 - Type annotations are complex, and you may see &'static mut a, which is not as good as ref[static[mut[a]]]
 - Modular programming a::b::c is not as simple and intuitive as a.b.c
 - Anonymous functions (closures) are |x|{dosth(x)} which is very strange. Now even js have syntax x=>...
 - OO-related struct: impl in each method must have self, which is not as good as writing self to impl, such as impl m1(self)

When trying to map Rust to Scala, we can see that:
 - |x|{dosth(x)} becomes x=>dosth(x)
 - &'static mut a becomes ref[static[mut[a]]]
 - a::b::c becomes a.b.c
 - let mut x=a becomes val x: MutRef = a
 - use Scala's match syntax 

This project is still in the early stages, please feel free to contribute your ideas and suggestions in the issues section.
