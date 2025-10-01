# Index

[License](#license)<br/>
[Introduction](#introduction)<br/>
[General Formatting](#general-formatting)<br/>
[Whitespace](#whitespace)<br/>
[Includes](#includes)<br/>
[Language Features](#language-features)<br/>
[Files](#files)<br/>
[Comments](#comments)<br/>
[The Importance of Code Styling](#the-importance-of-code-styling)<br/>
[Supporting Research](#supporting-research)

<br/>
<br/>
<br/>

# License

MIT License.

<br/>
<br/>
<br/>

# Introduction

This is my personal style guide.

It contains:
- The specifics of how my C++ code will be formatted.
- A `.clang-format` file to automatically format C++ code.
- A rant about why code styling is important.

<br/>
<br/>
<br/>

# General Formatting

1. Use spaces to indent code.
1. A tab is equal to 4 spaces.
1. The maximum length of a line shall be 80 characters.
1. Every variable must be declared on its own line.
1. Use snake case to name everything.
1. Use the Allman bracing style.
    1. A single statement control structure must still use Allman braces.
    1. A single statement function must still use Allman braces.

<br/>
<br/>
<br/>

# Whitespace

1. Statement keywords must be followed by a single space.
1. Comma operators must be followed by a single space.
1. Binary and ternary operators have a single space on both sides of the operator.
1. Pointer or reference operators shall have no space between it and the type, and a single space between it and the variable name.
1. Do not put whitespace at the end of a line.
1. Do not put whitespace between function names and the opening parenthesis.
1. Do not put whitespace between unary operators and their argument.
1. Do not use whitespace with member access operators.
1. Do not put whitespace between template or cast types and the angle brackets.
1. Insert a single blank line between functions.
1. Do not start or end functions with a blank line.
1. Indent access specifiers by 2 spaces.

<br/>
<br/>
<br/>

# Includes

Includes shall be organized as follows:
1. The first group of includes shall be the associated header file if it exists followed by a space.
1. The second group of includes shall be any includes that use angle brackets followed by a space.
1. The third group of includes shall be any other includes followed by a space.

In addition:
1. If a file uses a header directly, include it directly.

<br/>
<br/>
<br/>

# Language Features

1. Prefer double over floats.
1. Prefer nullptr over NULL or 0.
1. Prefer alias declarations over typedefs.
1. Prefer `#pragma once` over include guards.
1. Prefer west const over east const.
1. Use auto where it reduces typing and improves readability.
    1. Include explicit pointer and reference operators with auto.

<br/>
<br/>
<br/>

# Files

1. Strive to keep files under 500 lines.
1. File names shall match the type defined in the file.
1. Files shall define a single type.
    1. Nested types are acceptable.

<br/>
<br/>
<br/>

# Comments

1. Comments must add useful information to the surrounding code.
1. Comments must not be used for vertical whitespace.
1. Comments must not document language features.
1. TODO comments must document exactly what needs to be done and why.

<br/>
<br/>
<br/>

# The Importance of Code Styling

## Foreword

Almost everyone has the opinion that code styling is important because it improves readability, maintainability, and refactorability. However, very few blog posts, forums, stack exchanges, content creators, AI models, and white papers offer objective evidence that code styling directly affects these metrics.

Unfortunately, I am no exception.

I will share my experience with code styling and make hypotheses. However, these hypotheses will need to be confirmed by someone more intelligent, more funded, and more disciplined than myself. If anyone has evidence proving or disproving my hypotheses, please reach out. Finally, I've made an effort to document resources of interest in [Supporting Research](#supporting-research).

<br/>

## Reduced Cognitive Overhead

Most engineers have a preference when it comes to indentation style. Objectively, no style is better than another. However, engineers often feel their preference is the best because that's what they're comfortable with.

With that in mind, imagine a codebase that lacks a style guide entirely. This allows engineers to write their code in their style. When said engineers have to understand different parts of the codebase, they're likely to experience discomfort for a few reasons:
1. The code is not in their style
1. The code has no clear starting point
1. The code does not document major components
1. The code does not clearly articulate program flow
1. The code does not document function or variable purpose

In other words, there's a ton of cognitive overhead associated with understanding code. Having a consistent style guide can reduce that cognitive overhead by one factor. Admittedly, code style may not be the most significant factor but nonetheless is a contributor.

In summary, my hypothesis is that a consistent style guide reduces an engineer's cognitive overhead as they explore unfamiliar code. This leads to improved readability.

<br/>

## Improved Outlook

Identical to the above situation, imagine a codebase that lacks a style guide entirely and allows engineers to write their code in their style. This creates a mental barrier of code ownership. For example, an engineer who writes code in their style considers that "their code". Similarly, any portion of the codebase that's not in their style is considered "not their code". This is a bad mindset. Engineers should consider the entirety of the codebase "our code" and always strive to write the best code "we" can. I'm of the opinion that a codebase following a consistent style guide promotes the "our code" mindset. Any team that can make the following statement likely has a greater sense of community than teams that cannot:
- "We as a team have collectively decided how our code will be styled and we are all going to make an effort to maintain that style."

In summary, my hypothesis is that a consistent style guide creates a greater sense of community on teams and encourages contributors to view the codebase as a shared effort.

<br/>

## Improved Morale

When code is inconsistently formatted, it's ugly. Ugly code can make it "feel" like bad code. Bad code breeds more bad code. In other words, when engineers need to modify ugly code, their morale is reduced and they're more likely to write ugly code themselves. Stop me if you've heard this before: "Ugh, this code is so bad. We should really clean this up, but we don't have time. Let me just make the needed change and get out of here.". That morale reduction spreads throughout the codebase from not just style, but to optimization as well. I am of the opinion that having a consistent style guide can improve attitude toward the code and inspire engineers to write better code.

On the topic of beautiful code, the human brain comes equipped with pattern matching. Consistently styled code provides the brain with familiar patterns and unconsciously creates a better feeling toward the code. Imagine a codebase that consistently uses the Allman bracing style. If the brain can always expect an opening curly brace on the line after a function signature, it creates a rhythmic satisfaction as it progresses through multiple functions.

All the above points are best shown through the following example. If we had to modify code in the following blocks, consider the following questions:
1. Which block inspires us to write better code?
1. Which code is easier to read?
1. Which code "feels" better?

**Unformatted:**
```c++
bool is_even(int i) { return i % 2 == 0; }

void contains()
{
const auto arr = {1, 2, 3, 4};
    const auto to_find = {3, 5};

    for (const int val : to_find)
        if (std::find(arr.begin(), arr.end(), val) == arr.end()) std::cout << "arr does not contain " << val << '\n';
        else
        {
            std::cout << "arr contains " << val << '\n';
        }
}

void predicate()
{
    const auto matrix = {std::array{3, 1, 4}, {1, 3, 5}};
    for (const auto& val : matrix)
    {
        const auto it = std::find_if(val.begin(), val.end(), is_even);
        if (it != val.end())
        {
            std::cout << "matrix contains an even number " << *it << '\n';
        }
        else std::cout << "matrix does not contain even numbers\n";
    }
}
```

**Formatted:**
```c++
bool is_even(int i)
{
    return i % 2 == 0;
}

void contains()
{
	const auto arr     = {1, 2, 3, 4};
	const auto to_find = {3, 5};

	for (const int val : to_find)
    {
        if (std::find(arr.begin(), arr.end(), val) == arr.end())
        {
            std::cout << "arr does not contain " << val << '\n';
        }
		else
        {
            std::cout << "arr contains " << val << '\n';
        }
    }
}

void predicate()
{
	const auto matrix = {std::array{3, 1, 4}, {1, 3, 5}};

	for (const auto& val : matrix)
    {
		const auto it = std::find_if(val.begin(), val.end(), is_even);

		if (it != val.end())
        {
			std::cout << "matrix contains an even number " << *it << '\n';
		}
        else
        {
            std::cout << "matrix does not contain even numbers\n";
        }
	}
}
```

In summary, my hypothesis is that a consistent style guide improves morale, improves readability, and inspires engineers to write better code.

<br/>

## Summary

I have created the following hypotheses. However, they currently exist as an opinion with little supporting evidence. They will need to be proven or disproven by someone more intelligent, more funded, and more disciplined than myself.
1. A consistent style guide reduces an engineer's cognitive overhead as they explore unfamiliar code. This leads to improved readability.
1. A consistent style guide creates a greater sense of community on teams and encourages contributors to view the codebase as a shared effort.
1. A consistent style guide improves morale, improves readability, and inspires engineers to write better code.

<br/>
<br/>
<br/>

# Supporting Research

Study:
- Research on the correlation between code readability and code indentation, syntax highlighting, and comments.

Highlights:
- Tested on 10 subjects with 1 to 5+ years experience.
- Utilized eye-tracking technology to monitor how subjects interacted with the code.
- Indentation, syntax highlighting, logical naming, and function comments has a noticable improvement on code readability and understanding.
- This is code formatting, not code styling.

Reference:
- Kanoutas, T., Karanikiotis, T., & Symeonidis, A. L. (2024). Enhancing code readability through automated consistent formatting. Electronics, 13(11), 2073. https://doi.org/10.3390/electronics13112073

<br/>
<br/>

Study:
- Research on the correlation between code readability and code style.

Highlights:
- Mathematically links code style to readability to determine if there's a correlation.
- Frankly, this lacks a human element and practicality.
- However, mathematically the following is notable:
    - There is a correlation between code style (aka beauty) and readability.
    - Code style (aka beauty) contributes to intellectual and emotional satisfaction.
    - Cognitive load is related to the density of operators and operands, logic complexity, lines of code, statement length, number of statements, etc.

Reference:
- Coleman, R. (2018). Aesthetics versus readability of source code. International Journal of Advanced Computer Science and Applications, 9(9). https://doi.org/10.14569/ijacsa.2018.090902

<br/>
<br/>
<br/>
