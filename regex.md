# Regex Tutorial

This is an in depth explanation of the use of Regular Expressions or RegEx.
I will be using the following regex for the purposes of explaining each components function. 
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
The regex above is for matching an email address.

## Summary

Regular expressions are a sequence of characters that define a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### **Anchors**

Anchors are regex tokens that don't match any characters but that say or assert something about the string or the matching process.

^ (caret) matches the beginning of a string

\$ (dollar sign) matches the end of a string

### **Quantifiers**

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.

\* (asterisk) matches anything in the place of the *, or a "greedy" match

\+ (plus sign) matches the character before the + one or more times

? (question mark) matches the character before the ? zero or one times, or a "non-greedy" match

{x,y} matches a string that has between x and y of the preceding tokens

### **OR Operator**

| an OR character

### **Character Classes**

Specifies the characters that will successfully match a single character from a given input string.

\w is word (program identifier) character: [A-Za-z0-9_]

\W is non-word character: [^A-Za-z0-9_]

\s is a whitespace character: [ \f\n\r\t]

\S is a non-whitespace character: [^ \f\n\r\t]

\d is a digit character: [0-9]

\D is a non-digit character: [^0-9]

. matches any character as a wildcard

### **Flags**

A flag is an optional parameter to a regex that modifies its behavior of searching.

i (ignore casing) makes the expression search case-insensitive

g (global) makes the expression search for all occurences

s (dot all) makes the wild character . match newlines as well

m (multiline) makes the boundary characters ^ and $ match the beginning and ending of every single line instead of the beginning and ending of the whole string

y (sticky) makes the expression start its searching from the index indicated in its lastIndex property

u (unicode) makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well

### **Grouping and Capturing**

Capturing groups are a way to treat multiple characters as a single unit.

() (parenthesis) captures a group with a given value

### **Bracket Expressions**

A bracket expression is either a matching list expression or a non-matching list expression. 
It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions.

 [] (brackets)

### **Greedy and Lazy Match**

Greedy means matching the longest possible string.

Lazy means matching the shortest possible string.

### **Boundaries**

\b represents an anchor like caret (it is similar to $ and ^) matching positions where one side is a word character (like \w) and the other side is not a word character (for instance it may be the beginning of the string or a space character).

\B is its negation and matches all positions where \b doesn’t match and could be if we want to find a search pattern fully surrounded by word characters.

### **Back-references**

Backreferences match the same text as previously matched by a capturing group.

\1

### **Look-ahead and Look-behind**

Lookahead and lookbehind are zero-length assertions just like the start and end of a line, and start and end of word anchors.
They do not consume characters in the string, but only assert whether a match is possible or not.

(?=)

(?<=)

## **Email RegEx Match Analysis**

The following regular expression is for matching an email address.

```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

It is important to note that the forward slashes (`/`) at the beginning and end of the regex simply denote the boundaries or beginning and end of itself.

```
/^([a-z0-9_\.-]+)@
```

For the first grouping above, characterized by being wrapped in parentheses `()`, the `^` denotes the beginning of the string to be matched. Parentheses used in a regular expression not only group elements of that expression together, but also designate any matches found for that group as *tokens*. We can see there is a bracket expression with a set of ranges and literal characters to be matched. `([a-z` (matches lowercase letters from a-z) `0-9` (matches digits from 0-9) `_` (matches the literal character underscore) `\.` (an escaped character, matching the literal character period or dot) `-` (matches the literal character dash) `]+)`. The quantifier `+` will match one or more of the preceding *token*. Finally, the `@` outside the parentheses will be matched only once in this expression as a literal character.

```
([\da-z\.-]+)\.
```

For the second grouping above, we can see there is another bracket expression with a set of ranges and literal characters to be matched. `([\d` (matches any digit character) `a-z` (matches any lowercase letters from a-z) `\.` (an escaped character, matching the literal character period or dot) `-` (matches the literal character dash) `]+)\.`. The quantifier `+` will match one or more of the preceding token.

```
([a-z\.]{2,6})$/
```

For the third grouping above, there is a bracket expression with a set of letters to be matched, as well as a quantifier with a numerical range. `([a-z` (matches any lowercase letters from a-z) `\.` (an escaped character, matching the literal character period or dot) `]` `{2,6}` (a quantifier that will match only 2 to 5 of the preceding tokens) `)$/` and finally, a `$` which denotes the end of the string to be matched.
