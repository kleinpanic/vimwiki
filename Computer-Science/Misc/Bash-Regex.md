# Bash Regex
## Basics 
- Regex means regular expression. 
### Overview
- Regex is short for regular expression, is a sequence of characters that define a search pattern for text manipulation or pattern matching. In Bash Regex is used within commands like grep, sed, awk, and even within parameter expansions and conditional expressions. A regular expression comprises one or more elemenets such as:
    * Character Set: The character set in regex is a group of specific characters treated as their literal meaning. They doont have any specific meaning or function with the regex. For Example, if you include the character set [abc] in a regex, it will match any occurance of 'a', 'b', or 'c', in the text
    * Anchors: Anchors in regex are special symbols used to mark specifc positions in the text where the pattern should match. They don't represent actual characters but rather indicate where the pattern begins or ends within the text. Two common anchors in regex are caret (^) and dollar signs($)
    * Modifiers: Modifiers in regex are special symbols or characters that expand or narrow the range of text that the regex patttern can match. Some common modifiers are `+`, `*`, `?`. 
### Types of Regex in bash
- In bash there are two types of regular expressions (regex) mostly ised:
    1. Basic Regular Expression (BRE): BRE is the default regex type used in many traditional unix utilities like grep, sed, and awk. in BRE, certain metacharacters such as ?, + , | , and () are treated as literals unless escaped with a backslash \. BRE is suitable for basic pattern-matching tasks and is widely supported across unix based systems
    2. Extended Regular Expression (ERE): ERE is an enhanced version of BRE that offers a broader range of metacharacters and features. In ERE, metacharacters such as ? , + , | , and () ae interpreted with their special meanings by default without needing to escape them. ERE supports additional features like quantifiers (?, +, {}) and backreferences (\1, \2, etc). Utilities like grep -E (or egrep) and sed -E explicitly supports EREs. ERE offers shorter and more expressive regex patterns as compared to BRE. This makes 
