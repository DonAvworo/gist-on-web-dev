# Title Regex-Gist

A regex or regular expression is a theoretical computer science and formal language theory. in the context of this tutorial, a regular expression is a sequence of characters that define a search pattern. Regular expressions are used to find a match between a text string and a pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

## Summary

In this tutorial, we will be using regular expressions to validate user input. We will be using the following regex to validate user input: `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`. This regex will validate an email address. The regex will be broken down into components (not same as the Regex Components section below):

## Table of Contents

- [Summary](#summary)
- [Table of Contents](#table-of-contents)
- [Regex Components](#regex-components)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Email Validation](#email-validation)
- [Conclusion](#conclusion)
- [Author](#author)
- [References](#references)

## Regex Components

The following characters or groups of characters are used to validate the email address:

- `^`               - The start of the string
- `([a-z0-9_\.-]+)` - This is the first group of characters that will be matched.
                      The characters that will be matched are a-z (lowercase), 0-9, underscore, period, and hyphen.
- `@`                - The at symbol is used to match the @ symbol.
- `([\da-z\.-]+)`    - This is the second group of characters that will be matched.
                      The characters that will be matched are 0-9, a-z (lowercase), period, and hyphen.
- `\.`               - The period is used to match the period.
- `([a-z\.]{2,6})`   - This is the third group of characters that will be matched.
                      The characters that will be matched are a-z (lowercase) and period.
- `$`                - The end of the string  

But first we need to understand the basics of regex and how to use it.

What are the components of a regex?

The components of a regex are as follows:
[Anchors](#anchors), [Quantifiers](#quantifiers), [Grouping Constructs](#grouping-constructs), [Bracket Expressions](#bracket-expressions), [Character Classes](#character-classes), [The OR Operator](#the-or-operator), [Flags](#flags), and [Character Escapes](#character-escapes).

### Anchors
    - Anchors are used to match a position within the string. There are two types of anchors: the caret `^` and the dollar sign `$`. The caret matches the beginning of the string, while the dollar sign matches the end of the string.

### Quantifiers
    - Quantifiers are used to match the number of characters within the string. There are five types of quantifiers: the asterisk `*`, the plus sign `+`, the question mark `?`, the curly braces `{}`, and the pipe `|`. The asterisk matches zero or more characters, the plus sign matches one or more characters, the question mark matches zero or one character, the curly braces match a specific number of characters (eg {n} matches exactly n times), and the pipe matches one of several characters (eg a|b matches either a or b).

### Grouping Constructs
    - is used to match a group of expression or subexpression within the string. Repeated input of the same expression can be replaced with a grouping construct. 

### Bracket Expressions
    - Bracket expressions are used to match a single character within the string. There are two types of bracket expressions: the square brackets `[]`, and the curly braces `{}`and the parentheses `()`. The square brackets match a single character, the curly braces match a range of characters, and the parentheses match a set of characters.
    
    The square brackets match a single character, and the curly braces match a range of characters.

### Character Classes
    - Character classes - are used to match a single character within the string. There are three types of character classes: the period `.`, the square brackets `[]`, and the backslash `\`. The period matches any character, the square brackets match a specific character, and the backslash matches a special character.

### The OR Operator 
    - The OR operator is used to match one of several characters within the string. There are two types of the OR operator: the pipe `|`, and the square brackets `[]`. The pipe matches one of several characters, and the square brackets match a specific character.

### Flags
    - Flags - are used to modify the search behavior. There are three types of flags: the global `g`, the case insensitive `i`, and the multiline `m`. The global flag matches all occurrences of the pattern, the case insensitive flag matches both uppercase and lowercase characters, and the multiline flag matches all occurrences of the pattern in multiple lines.

### Character Escapes
    - Character escapes are used to match a special character within the string. The backslash `\`, matches a special character that follows it.  For example, a brace ({) begins the definition of a quantifier, but a backslash followed by a brace (\{) matches a literal brace.


## Email Validation
The list below summarises the functions of characters in the regex components:

- The caret `^` matches the beginning of the string.
- The dollar sign `$` matches the end of the string.
- The `+` matches one or more of the preceding token.
- The `.` matches any character except a newline.
- The `[]` matches any character in the brackets.
- The `()` matches the regular expression inside the parentheses.
- The `{}` matches the number of times specified by the number inside the curly braces.
- The `|` matches one of several characters.
- The `\` any character that is between the backslash (beginning of the string and the end of the string) is treated as a literal character and are the regex components.

Considering what we have learnt thus far, we can now break down how the regex can be used to validate an email address.

The caret `^`is an indication that the string must start with the characters that follow the caret. In this case, the string must start with the characters `^([a-z0-9_\.-]+)` where the characters that will be matched are a-z (lowercase), 0-9, underscore, period, and hyphen. Remember that the characters that follow the caret are the first group of characters that will be matched and as was outlined above the `+` indicates that the characters that follow the caret must be matched one or more times. The `+` is a quantifier.

Now if a user inputs a character that is not in the list of characters that follow the caret, the string will not be validated. For example, if a user inputs the character `@` instead of the characters contained in first group eg. `a`, the string will not be validated.

So in our email address validation example, @email.com will not be validated because the string does not start with the characters `^([a-z0-9_\.-]+)`. But email@com will be validated because the string starts with the characters `^([a-z0-9_\.-]+)`.

The at symbol `@` is used to match the at symbol. The at symbol is the second group of characters that will be matched. The at symbol is a character class. so in our email address validation example, email.com will not be validated because the string does not contain the at symbol `@`. But email@domain.com will be validated because the string contains the at symbol `@`. 

In our email above (email@domain.com), the '.' (period or dot) after the domain is the third group of characters that will be matched. The '.' (period) is a character class. So in our email address validation example, email@domain will not be validated because the string does not contain the period `.`. But email@domain.com will be validated because the string contains the period `.`.

The `$` is an indication that the string must end with the characters that precede the dollar sign. In this case, the string must end with the characters `([a-z\.]{2,6})$` where the characters that will be matched are a-z (lowercase) and period and that the characters must be matched between 2 and 6 times. The `{2,6}` is a quantifier. So in our email address validation example, e@domain.COM will not be validated because the string does not end with the characters `([a-z\.]{2,6})$` though the number of times the characters are used meets the criteria. However, capital cased letters are not specified in the expression. The email address email@domain.com will be validated because the string ends with the characters `([a-z\.]{2,6})$`.

In summary, the regex expression `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$` will validate the following email addresses:

- email123@domain.com
- emailme.123@domain.com
- donotreply@domain.com

But will not validate the following email addresses:

- email@domain
- email@domain.
- @domain.com 

## Conclusion:

in conclusion, using a regex or Regular Expression is a great way to validate user input. It is a great way to ensure that the user input is in the correct format. It is also a great way to ensure that the user input is not empty. It is like using an 'if' statement or ternary operation (another scope of topic but can relatively be used in same way as regex) in javascript to determine if the user input is empty or not or input is in the correct format or not. like so:

`if (userInput === ['a', 'b', 'c', '0', '1', '3', '_', '\' && userInput !== '') {`  

`// validate user input`

`} else {`

`// do not validate user input`

`}`

Regular expressions are extremely useful in extracting information from text such as code, log files, spreadsheets, or even documents. Regular expressions can be used to find text, replace text, and validate user input. In the example above, we used regular expressions to validate user input of an email. 

Other uses of regular expressions include:
- extract the address from a string of text.
- extract the phone number from a string of text.
- extract the date from a string of text.
- extract the time from a string of text.
- extract the name from a string of text and so on.

Thank you for reading. I hope you found this tutorial helpful. If you have any questions or comments, please feel free to leave them below. I will be happy to answer them.

## Author

I am [Don Avworo](https://github.com/DonAvworo) (please click on the name to view my GitHub profile), a student of manchester university, currently studying a Full-Stack Web Development programme. I am very interested in creativity and programming have opened up a new array of possibilities to create applications that will impact the world in a very positive way. I am very passionate about programming and I am always looking for new ways to improve my skills and learn new things. I am very excited to be part of the tech community and I am looking forward to learning and growing with you all. I am always working on a project and currently working  on a project called [The Tech Blog] Please contact me for any collaboration or if you have any questions. I am always open to new ideas and opportunities.

## References
 
 * https://docs.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions

 * https://www.bing.com/videos/search?q=regex&&view=detail&mid=6A2DFEBA63E7F62A723A6A2DFEBA63E7F62A723A&&FORM=VRDGAR&ru=%2Fvideos%2Fsearch%3Fq%3Dregex%26FORM%3DHDRSC3

 * https://www.youtube.com/watch?v=rhzKDrUiJVk

 * https://en.wikipedia.org/wiki/Regular_expression

 * https://regex101.com/

 * https://www.computerhope.com/jargon/r/regex.htm

 * https://www.w3schools.com/python/python_regex.asp