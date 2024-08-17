# A Complete, and Comprehensive guide to markdown:

## Overview: 
- Markdown is fucking lit. It's an open file format (a file format for storing digital info defined by open source/ publcated specifications, usually maintained by a standards organization), lightweight, markup language, used for creating a basic formatted text output, using a plain-text editor. It was created in 2004, and is designed to be easy to read, write, and comprehend. Normal file extention for markdown files is a .md or a .markdown (even though names should not be LAOD BEARING!). 
- Markdown in a text editor format looks a lot like a basic text file, with various characters to define different formats when viewed in a Website format. Markdown can be translated directly into HTML, and thus can be translated into a website view. Things like lists, headings, columns, rows, and more. 
- There are many different variations of Markdown, and the most prolific is "Github Flavored Markdown" which github implimented in early 2009. This added support for shit like tables, and nesting block content inside list elemets. 

## Basic Syntax: 

### Headings: 

| Markdown          | HTML          | Rendered Output (Website equivalent)    |
|-------------------|---------------|-----------------------------------------|
| # Heading lvl 1   | <h1>Txt</h1>  | Look at the top heading                 |
| ## Heading lvl 2  | <h2>Txt</h2>  | Look at the smaller headings under that |
| ### Heading lvl 3 | <h3>Txt<h/h3> | Look at the smaller ones (e.g Headings) |
|-------------------|---------------|-----------------------------------------|
| Alt Markdown      | HTML          | Rendered Output                         |
|-------------------|---------------|-----------------------------------------|
| Heading level 1   | <h1>Txt</h1>  | Same as before (Top heading)            |
| ================= |               |                                         |
| Heading level 2   | <h2>Txt</h2>  | Same as before                          |
| ----------------- |               |                                         |
|-------------------|---------------|-----------------------------------------|

#### Best practices for heading:

- Markdown will not always agree on how to handle missing space between the hashtang and the heading name. For standardization, ensure a space is between the hashtag and the first letter. 
  - Dont: #Header
  - Do: # Header

- For a standardized look, ensure there is space before and after header lines. 
  
### Paragraphs:

- By far, the easiest fucking syntax. Literally what this shit is is just a paragraph. Just write normally as if you were writing in a txt file. 
  
| Markdown | HTML        | Rendered Output (Website equivalent) |
|----------|-------------|--------------------------------------|
| TEXT     | <p>TEXT</p> | TEXT                                 |
|----------|-------------|--------------------------------------|

#### Best practices for paragraphs:

- Dont indent you paragraphs before writing. Make sure its all left indented, uneless you are using shit like lists. Do not tab or add spaces in front of paragraphs. 
  
### Line breaks:

- To create a line break, or text on a new line, just enter return

| Markdown | HTML                    | Rendered Output (Website equivalent) |
|----------|-------------------------|--------------------------------------|
| Line 1   | <p>Line 1<br>Line 2</p> | Line 1                               |
| Line 2   |                         | Line 2                               |
|----------|-------------------------|--------------------------------------|

#### Line break best practices

- Generally you should use two or more spaces (Commonly called trailing whitespace) for line breaks but each markdown applicator is a little different in how it handles trailing whitespace, so learn your system. I use nvim and I personally don't do it, and I don't think it's important for most purposes, however it is normally the advice that is given. 
- Don't use CommonMark syntax like backslashes, or HTML syntax like "<br>". I'm gonna be honest I feel like that's pretty obvious, we're writing in markdown not fucking CommonMark. 

### Emphasis

- Want to add some emphasis to your message? Markdown got you covered dawg.

#### Bold

| Markdown      | HTML                       | Rendered Output (Website equivalent) |
|---------------|----------------------------|--------------------------------------|
| **Bold Text** | <strong>Bold Text</strong> | **Bold Text**                        |
| __Bold Text__ | <strong>Bold Text</strong> | __Bold Text__                        |
| **Bold** Text | <strong>Bold</strong>Text  | **Bold** Text                        |
|---------------|----------------------------|--------------------------------------|

- In case it's not showing up bc it's in a table, here is **Bold** text. 
It's best to use astrerisks in most cases as using underscores in the middle of words is not supproted in markdown (or at least most renditions)

#### Italic

| Markdown       | HTML                  | Rendered Output (Website equivalent) |
|----------------|-----------------------|--------------------------------------|
| *Italic*       | <em>Italic</em>       | *Italic*                             |
| _Italic_       | <em>Italic</em>       | _Italic_                             |
| *Italic* Words | <em>Italic</em> Words | *Italic* Words                       |
|----------------|-----------------------|--------------------------------------|

- I'm writig everything in a table for better output and looks but *Italic* words look like that. 
- As you can clearly see, Markdown is goated. Again just like bold, dont use underscores in the middle of a sentice, use asterics. 

#### Now get ready... for BOTH!

- You wanna say some really emphasized shit?? Mark down, once again, has graced us from the heavens, to meet our demands. ***I CANNOT Possibly Underestimate How Goated this is***. 
  
| Markdown  | HTML                         | Rendered Output (Website equivalent) |
|-----------|------------------------------|--------------------------------------|
| ***TXT*** | <em><strongTXT</strong></em> | ***TXT***                            |
| ___TXT___ | <em><strongTXT</strong></em> | ___TXT___                            |
| __*TXT*__ | <em><strongTXT</strong></em> | __*TXT*__                            |
|-----------|------------------------------|--------------------------------------|
- Aight you get the point, or at least hopefully you do, because we are ***MOVING THE FUCK ON***
### Blockquotes

- Blockquotes are special renditions specific to website formats. 
- Blockquotes are created by adding a ">" in front of a paragraph
> A blockquote looks like this. 
- Blockquotes with multiple paragraphs can be rendered, with a line break, by including an empty line in the block quote (putting > in front of an empty line, after the first section of the paragraph and before the second).
> Multiple 
>
> Paragraphs

##### Blockquote specials

- Nested blockquotes can be created by adding a >> in front of the paragraph you desire to be nested. Example would be 
    - > Line 1
    - > 
    - >> Nested Line
- It'll go a little bit like:
> Line 1
>
>> Nested Line

- Blockquotes with other elements can be created, such as Headers, lists, and emphasis by just including it in the syntax. 
    - > #### Header 4
    - > 
    - > - List 
    - > *ITALIC* and **BOLD** and ***BOTH***
    - >> A fucking nested blockquote with ***EMPHASIS***
- it'll look like:
> #### Header 4
>
> - List
> *ITALIC* and **BOLD** and ***BOTH***
>> A fucking nested blockquote with ***EMPHASIS*** 

### Lists of various kinds!

- Among other things, as you may have noticed, markdown allows you to create a lists! And not only does it allow us to create a list, it allows us to create MANY! Aight lets get into it 

#### Ordered Lists

| Markdown  | HTML                | Rendered Output (Website equivalent) |
|-----------|---------------------|--------------------------------------|
| 1. First  | <ol>                | 1. First                             |
| 2. Second | <li> First... </li> | 2. Second                            |
| 3. Third  | </ol>               | 3. Third                             |
|-----------|---------------------|--------------------------------------|

#### Unordered lists

- Now unlike ordered lists, unordered lists have multiple syntax options. 
  
| Markdown  | HTML                | Rendered Output (Website equivalent) |
|-----------|---------------------|--------------------------------------|
| - First   | <ul>                |  First                             |
| * Second  | <li> First... </li> |  Second                            |
| + Third   | </ul>               |  Third                             |
|-----------|---------------------|--------------------------------------|

- I can't render the dot it creates but it creates a dot, regardless of what type of syntax option you use. Best practice is to not mix and match the 3 different options in 1 list like i just did, but i just wanted to show you all the options. 
- Here is what a list looks like 
  - Firt
  * Second
  + Third

### Code Blocks

- Code blocks are traditionally indented four spaces or with 1 tab. When in a list, they are indented by a factor of that based on their location. 
- Example: Open a file
- Write some shit in that fike
        <html>
            <head>
            <title></title>
            </head>
- save the file

### Code

- To denote a word or phrase as code enclose it in backticks
- Example:
    - 'nvim'

### Escaping Backticks

- If the word or phrase you want to denote includes one or more backticks, you can escape it by enclosing the word or phrase in double backticks ('')
    - ''Use 'nvim' to edit your markdown files!''

### Horizontal Rule

- To create a horizontal rule, you can use three or more asterisks or dashes or underscores, on a line by themselves.
- Examples:
    ***
    ---
    ___

### Links

- To create a link, enclose the text in brackets, and then follow it with the URL in parentheses. 
[Checkout My github](https://github.com/kleinpanic)

### Images

- I know what you're thinking, ***NO WAY MARKDOWN SUPPORTS IMAGES*** and guess what, you're wrong. To create an image link, make sure the file is located somewere on your personal drive and that your editor has priveledges to the location. Put an exclamation park in front of words enclosed by brackets, followed by a path to the file encapsulated in parentheses. 
  
| Mark Down                  |
|----------------------------|
| ![Image](/pathtoimage.png) |
|----------------------------|
- Pretty fucking cool I know. 
 
 ## VimWiki Extention










