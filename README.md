# Index

[License](#license)<br/>
[Introduction](#introduction)<br/>
[Using This Style Guide](#using-this-style-guide)<br/>
[The Importance of Code Styling](#the-importance-of-code-styling)<br/>
[Supporting Research](#supporting-research)

<br/>
<br/>
<br/>

# License

See [LICENSE](./LICENSE)

<br/>
<br/>
<br/>

# Introduction

This is my personal style guide.

The [c](./c) and [cpp](./cpp) folders will contain the following:
1. A `style-guide.md` file which documents guidelines that must be adhered to.
1. A `.clang-format` file to automatically format code to abide by the guidelines.
1. A `.clang-tidy` file to lint code to abide by the guidelines.

Below documents how to use this style guide and a rant about why styling is important.

<br/>
<br/>
<br/>

# Using This Style Guide

To use this style guide:
1. Clone the repository into a directory of your choice.
1. In the root folder of a C project, create symbolic links to `c/.clang-format` and `c/.clang-tidy`.
1. In the root folder of a C++ project, create symbolic links to `cpp/.clang-format` and `cpp/.clang-tidy`.
1. Add the symbolic links to `.gitignore`.
1. Update the IDE of choice to use clang for formatting and linting.

At that point, the project should have everything required to automatically format and lint code to abide by this style guide.
To update to the latest style guide, pull the latest of this repository.

<br/>
<br/>
<br/>

# The Importance of Code Styling

## Foreword

Almost everyone has the opinion that code styling/linting is important because it improves readability, maintainability, and refactorability. However, very few blog posts, forums, stack exchanges, content creators, AI models, and white papers offer objective evidence that code styling/linting directly affects these metrics.

Unfortunately, I am no exception.

I will share my experience with code styling/linting and make hypotheses. However, these hypotheses will need to be confirmed by someone more intelligent, more funded, and more disciplined than myself. If anyone has evidence proving or disproving my hypotheses, please reach out. Finally, I've made an effort to document resources of interest in [Supporting Research](#supporting-research).

<br/>

## Reduced Cognitive Overhead

Most engineers have a preference when it comes to indentation style. Objectively, no style is better than another. However, engineers often feel their preference is the best because that's what they're comfortable with.

Imagine a codebase that lacks a style guide entirely. This allows engineers to write their code in their style. However, when engineers have to understand parts of the codebase that are not in their style, they're likely to experience discomfort. This adds unnecessary cognitive overhead when trying to understand different parts of a codebase.

Conversely, a consistent style guide would remove this cognitive overhead allowing engineers to experience more comfortability when exploring unfamiliar code.

In summary, my hypothesis is that a consistent style guide reduces an engineer's cognitive overhead as they explore unfamiliar code leading to improved readability.

<br/>

## Improved Outlook

Identical to the above situation, imagine a codebase that lacks a style guide entirely and allows engineers to write their code in their style. This creates a mental barrier of code ownership. For example, an engineer who writes code in their style considers that "their code". Similarly, any portion of the codebase that's not in their style is considered "not their code". This is a bad mindset. Engineers should consider the entirety of the codebase "our code" and always strive to write the best code "we" can. A codebase following a consistent style guide promotes the "our code" mindset. Any team that can make the following statement likely has a greater sense of community than teams that cannot:
- "We as a team have decided how our code will be styled and we are all going to make an effort to maintain that style."

In summary, my hypothesis is that a consistent style guide creates a greater sense of community on teams and encourages contributors to view the codebase as a shared effort.

<br/>

## Improved Morale

When code is inconsistently formatted, it's ugly. Ugly code can make it "feel" like bad code. Bad code breeds more bad code. In other words, when engineers need to modify ugly code, their morale is reduced and they're more likely to write ugly code themselves. Stop me if you've heard this before: "Ugh, this code is so bad. We should really clean this up, but we don't have time. Let me just make the needed change and get out of here.". That morale reduction spreads throughout the codebase from not just style, but to optimization as well. Having a consistent style guide can improve attitude toward the code and inspire engineers to write better code.

On the topic of beautiful code, the human brain comes equipped with pattern matching. Consistently styled code provides the brain with familiar patterns and unconsciously creates a better feeling toward the code. Imagine a codebase that consistently uses the Allman bracing style. If the brain can always expect an opening curly brace on the line after a function signature, it creates a rhythmic satisfaction as you progresses through multiple functions.

All the above points are best shown through the following example. If we had to modify code in the following blocks, consider these questions:
1. Which code inspires us to write better code?
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

In summary, my hypothesis is that a consistent style guide improves morale and inspires engineers to write better code.

<br/>

## Summary

I have created the following hypotheses. However, they currently exist as an opinion with little supporting evidence. They will need to be proven or disproven by someone more intelligent, more funded, and more disciplined than myself.
1. A consistent style guide reduces an engineer's cognitive overhead as they explore unfamiliar code leading to improved readability.
1. A consistent style guide creates a greater sense of community on teams and encourages contributors to view the codebase as a shared effort.
1. A consistent style guide improves morale and inspires engineers to write better code.

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

Reference:
- Kanoutas, T., Karanikiotis, T., & Symeonidis, A. L. (2024). Enhancing code readability through automated consistent formatting. Electronics, 13(11), 2073. https://doi.org/10.3390/electronics13112073

<br/>
<br/>

Study:
- Research on the correlation between code readability and code style.

Highlights:
- Mathematically links code style to readability to determine if there's a correlation.
- Frankly, this lacks a human element and practicality.
- However, mathematically speaking, the following is notable:
    - There is a correlation between code style (aka beauty) and readability.
    - Code style (aka beauty) contributes to intellectual and emotional satisfaction.
    - Cognitive load is related to the density of operators and operands, logic complexity, lines of code, statement length, number of statements, etc.

Reference:
- Coleman, R. (2018). Aesthetics versus readability of source code. International Journal of Advanced Computer Science and Applications, 9(9). https://doi.org/10.14569/ijacsa.2018.090902

<br/>
<br/>
<br/>
