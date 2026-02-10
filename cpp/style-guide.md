# Index

[General Formatting](#general-formatting)<br/>
[Whitespace](#whitespace)<br/>
[Includes](#includes)<br/>
[Language Features](#language-features)<br/>
[Files](#files)<br/>
[Comments](#comments)<br/>

<br/>
<br/>

# General Formatting

1. Use spaces to indent code.
1. A tab is equal to 4 spaces.
1. The maximum length of a line shall be 80 characters.
1. Every variable must be declared on its own line.
1. By default, use `snake_case` for naming.
    1. Exception: Macros should be `UPPER_SNAKE_CASE`.
1. Use the Attach bracing style.
    1. A single statement control structure must still use Attach braces.
    1. A single statement function must still use Attach braces.

<br/>
<br/>

# Whitespace

Do Nots:
1. Do not put whitespace at the end of a line.
1. Do not put whitespace between function names and the opening parenthesis.
1. Do not put whitespace between unary operators and their argument.
1. Do not use whitespace with member access operators.
1. Do not put whitespace between template or cast types and the angle brackets.
1. Do not start or end functions with a blank line.

Always:
1. Always put a single space after statement keywords.
1. Always put a single space after comma operators.
1. Always put a single space on both sides of binary and ternary operators.
1. Always put a single space between pointer, reference, or universal operators and the variable name and no space between operators and the type.
1. Always put a single blank line between functions.
1. Always indent access specifiers by 2 spaces.

<br/>
<br/>

# Includes

Includes shall be organized as follows:
1. The first group of includes shall be the associated header file if it exists followed by a space.
1. The second group of includes shall be any includes that use angle brackets followed by a space.
1. The third group of includes shall be any other includes followed by a space.

Other include rules are:
1. If a file uses a header directly, it will include it directly.

<br/>
<br/>

# Language Features

Do Nots:
1. Do not nest ternary operators.
1. Do not delete null pointers as it results in a noop.
1. Do not include an else branch when the if statement returns from a function.
1. Do not use magic numbers in code.
    1. Exception: `0` is an acceptable magic number as it indicates no value. Even so, using `0` must be evaluated on a case by case basis. 
1. Do not use the inline keyword.

Always:
1. Always use traditional binary, unary, and overloaded operators.
1. Always match a function's parameter names in declaration and definition.
1. Always use auto where it reduces typing and improves readability.
    1. Include explicit pointer, reference, and forward reference operators with auto.
1. Always use uppercase letters when declaring literals.
1. Always use `#pragma once` instead of include guards.

Preferences:
1. Prefer double over floats.
1. Prefer nullptr over NULL or 0.
1. Prefer alias declarations over typedefs.
1. Prefer west const over east const.
1. Prefer `#ifdef` and `#ifndef` to `#if defined` and `#if !defined` respectively.
1. Prefer `std::flush` and newline characters to `std::endl`.

<br/>
<br/>

# Files

1. Files shall define a single type.
    1. Nested types are acceptable.
1. File names shall match the type defined in the file.
1. Strive to keep files as small and simple as possible (preferrably [0, 500] lines).

<br/>
<br/>

# Comments

1. Comments must add useful information to the surrounding code.
1. Comments must not be used for vertical whitespace.
1. Comments must not document language features.
1. TODO comments must document exactly what needs to be done and why.

<br/>
<br/>