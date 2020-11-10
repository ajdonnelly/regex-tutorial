# Title (replace with your title)

 The Common Email Id Regex

## Summary

In this tutorial you will learn how to match common email ids with a very useful and common regular expression, the common email id. Regex are most commonly employed either to comb through a large body of data, or to validate user inputted data? Need to validate emails, or urls, or  phone numbers, for example, then you need regex. If you need to validate data for email addresses, then you need this: /^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*$/. But what on earth are we looking at???

Regular expressions (commonly shortened to regex or regexp) are grouping of characters used to define a search pattern. Right now /^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*$/ may seem very intimidating, and even plain strange, but in this tutorial we will break down how this regex functions, is formed and how it's commonly used. By the end of the tutorial, you will be on your way to understanding a little more about and be on your way to creating and using your own regex! 

## Table of Contents

- [Delimiters](#delimiters)
- [Anchors](#anchors)
- [Character Literals](#character-literals)
- [Metacharacters](#meta-characters)
- [Escaping](#escaping)
- [Atoms](#atoms)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [OR Operator](#or-operator)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Backreferences](#backreferences)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

In this tutorial we will bread down our email id regular expression into its component parts to better understand how it works. 

### Delimiters

Regex really begin with what are called delimiters. They tell a program where the regex starts and where it ends. The most common delimiter is the slash (/) or forward slash.

The regex then is actually the string defined between two forward slashes (/). We can see that these two (/) delimiters exist in our email id regex at the begining and the end, and indicate the regular expression exists between the caret (^) and the dollar sign ($). 

/    ^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*$     /

### Anchors

While the forward slash delimiters define the boundaries of the regular expression, anchors, inside of the delmiters, define which characters are included in the search itself. Anchors are metacharacters that don't represent character literals. Instead they are used to match a speciifc position in a string. 

The two most common anchors are the caret (^) and the dollar sign ($). 

The (^) delineates the position at which the string begins. In our email id example this is the first parenthesis (() 

Meanwhile, the ($) dilineates the position at which the string ends. In our email id example this is the star (*).

So, the string inside the delimiters and the anchors is what we are actually searching for: ([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*

### Character Literals

A character literal is a letter, number or a symbol like a percentage sign or a group of the same. In our example [a-zA-Z0-9._%-] is a group of character literals bound by the metacharacters []. 

### Metacharacters 

Metacharacters are characters that have a special meaning when used in regular expressions. Escaping, discussed previously, is actually achieved with a metacharacter inside a string. Metacharachters generally fall into one of four categories: escaping, grouping, matching literal characters and quantifiers. The common metacharacters are {}[]()^$.|*+?\. Note that a regex with no metacharacters is no longer a regular expression, but a string literal. So, the group of charachter literals inside of the metacharacters [] that make up [a-zA-Z0-9._%-] are called a character class and just become the string literal a-zA-Z0-9._%- without these metacharacters. 

Note: most metacharacters won't work inside a character class. The only ones that do work are the backslash (\), the closing (]) and the (^). We’re going to talk about the caret in just a moment.

If you need to include one of these metacharacters as a character literal, you have to escape them using a backslash. So, for example, [\^] is a character class that matches a caret as a character literal.

### Escaping

 If your regular expression contains a metacharacter, you will need to escape that metacharacter to keep the program from confusing the search character with a metacharacter such as a delimiter. The backslash (\) is the escape character used in regular expressions. This tells the program to consider the slash as a literal slash and a part of the string to be searched for rather than as a delimiter bounding that string.

 For example, let’s say that you want to identify the use of HTTPS. Your regular expression with the default delimiter would be /https:\/\//. This is not the easiest thing to read as we end up having to escape every slash using a backslash. It takes some time getting used to.

 In our regex, we need to escape the metacharacter (.) immediatley preceing [a-zA-Z]{2,6})*$/, which identifies the pattern of the email extension that typically ends the email that follows the period, for example .com, .edu, .net etc. 

### Atoms 

Atoms are the subunits of the pattern that we want the processor to match and they can be character literals or metacharacters, as we previously discussed. For example, in our expression, the string literal bound by the metatacharacters [], [a-zA-Z0-9._%-] is a grouping of character classs consisting of atoms.  

### Quantifiers

Quantifier metacharacters tell the processor that you want to match multiple atom(s) immediately preceding the quantifier. 

The quantifiers in our expression are the two plus signs (+) that follow [a-zA-Z0-9._%-] and [a-zA-Z0-9.-]. The plus sign (+) quantifier tells the regular expression processor that you want it to match the preceding atom(s) 1 or more times in its search.  

### Bracket Expressions

Bracket Expressions ask the processor to run through and match any single character literal or character class from within the bracketed list or a range. The Email id regex has three bracket expressions: 
[a-zA-Z0-9._%-], [a-zA-Z0-9.-] and [a-zA-Z]. 

### Character Classes

As previosly discussed, the (+) quantifier seeks to match one or more of the atoms within the bracket expression [a-zA-Z0-9._%-]. However, this bracket expression contains multiple chracter classes or character sets. In this case, the processor is being asked to find one or more matches of one or more character literals between a and z, between A and Z, and one or more digits between 0 and 9, and one or more metacharacters of ._%-.

### OR Operator

The OR Operator (|) is a metacharacter that is not relevant to our regex but that is generally important and therefore needs to be discussed. It allows you to ask the processor to match either one or another regular expression pattern. For example, (?:>(.*)</\1> | \s+/>) is asking the processor to match either ?:>(.*)</\1> or \s+/>. 

### Flags

The closing delimiter can be followed by what's called a flag: 

Ignore case Flag

i : ignores the case(uppercase/lowercase) of the input string

Global Flag

g : instead of stopping at the first match, searches for multiple matches

### Grouping and Capturing

In our regex we have a pattern of multiple strings and quantifiers that we are asking the processor to check for repeatedly in either a dataset or validation. For example, the processor is asked to check for repeating patters of the groupings between the (), which is called a capturing group. The capturing group in our regex is  [a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}.

### Greedy and Lazy Match

Quantifiers give regex processors a choice between continually matching the preceding atom or matching it as few times as possible. These quantifiers are described as greedy and lazy quantifiers, respectively. A regular expression processor is by default always greedy. To prevent a greedy quanitfier from being greedy, add a question mark and the end of it. The quantifiers in our regex are inherently greedy but we have no need to make them lazy. 

### Backreferences

Backreferences essentially repeat an earlier (to the left) matched capturing group. They indicated by a \ followed by a number. There are no backreferences in our regex, but this is an important concept to know. 

### Breaking Down my Email

My email is a.james.donnelly@gmail.com. It matches the regex /^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6})*$/ because the a.james.donnelly matches [a-zA-Z0-9._%-]+ and precedes a (@) and the gmail portion matches [a-zA-Z0-9.-]+ and immediately precedes a (.) which is followed by com which matches [a-zA-Z]. 

### Breaking down the Common Email ID Regex

/ - this is the opening delimiter
^ - this is the opening anchor
( - this is the beginning of a capture group
[ - this is the beginnin of the first bracket expression
a-zA-Z0-9._%- - this is the string literal within the bracket expression. It consists of the character classes a-z, A-Z, 0-9 and the chracter literals ._%-. 
]+ - this is the end of the first bracket expression with a quantifier asking the processor to match one or more of the included character classes and character liters contained within the bracket expression.
@ - this is the character literal @ we're asking the processor to match. 
[a-zA-Z0-9.-]+ - this is the other bracket expression consisting like the one before of character literals and character classes. 
\. - this is the escaped metacharacter  (.) 
[a-zA-Z] - this is the last bracket expression consisting of two character classes. 

{2,6}

) - this is the close of the capture group. 
*
$ = this is the closing anchor
/ = this is the clsing delimiter

## Author

Alex Donnelly https://github.com/ajdonnelly/

