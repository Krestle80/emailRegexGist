# Regex Email Expression
### In this short gist the regex expresion:  
#### `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
### , whose primary purpase is to match for emails, will be broken down and explained bit by bit. To start a brief summary of what a regex expresion is. A regex expression is a set of search parameters that returns true or false when given a string. 
## Table of Contents
- #### [Boundries](##-Boundries)
- #### [Capturing Group](##-capturing-group)
- #### [Characater Classes](##-character-classes)
- #### [x{n,m} Quantifiers](##-quantifiers)
- #### [Questions](##-questions)



## Boundries
`/`<span style="color:red">^</span>`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})`<span style= 'color: red'>$</span>`/`

### The only boundaries in this regex expression are "`^`" and "`$`". They mark the begining "`^`" and end "`$`" of what you are looking for. They are always inclosed between two `/'s`.


## Capturing Group
`/^`<span style="color:red">(</span>`[a-z0-9_\.-]+`<span style="color:red">)</span>`@`<span style= 'color: red'>(</span>`[\da-z\.-]+`<span style= 'color: red'>)</span>`\.`<span style="color:red">(</span>`[a-z\.]{2,6}`<span style= 'color: red'>)</span>`$/`

### Parenthesis are used in order to define a capture group. They match for whatever is in between them. The lone characters in between them search for that specfic character only, see ['`\`'](##-character-classes) in Character Classes.
## Character Classes
`/^(`<span style="color:red;">[a-z0-9_\ .-]+</span>`)@([`<span style= 'color: red'>\da-z\.-]+</span>`)\.(`<span style= 'color: red;'>[a-z]</span>`\.{2,6})$/`
### Character classes are just how to use regex to look for specific paramaters. For example :
`/^[a-z0-9_]+&/`
### a simplfied part of the above function, the `[]` say that its listing paramaters, and then simply place what characters your're allowing for in between. Make sure to wrap any regex expression with `/'s` and the beginning and end boundries.  In this case `a-z` is a shorthand notation to allow all lowercase letters (instead of putting the shorthand you could type out every letter from a to z), `0-9` is shorthand to allow all integers (the `\d` in the second capture group is also a shorthand for allows all intergers), and `_` allows all underscores . This regex expression would therfore output true for any string that contained any combination of lowercase letters, intergers, or underscores.

###      


`/^[a-z0-9_`<span style= ' color: red;'> \ . -</span>`]+$/`

###
### the `\` in the expresion above makes the regex expresion refer to the next character specially, in this case it causes the `.` to match any `-` along with the character before it, so long as there is at least one other character before it. Instead of just matching for all `.'s`. Ironically the first two `\.` of the main regex expression do the opposite of this one :
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)`<span style= 'color: red;'> \ . </span>`([a-z\.]{2,6})$/`
### this is because outside of a character class `[]` the period is assumed to match the next character as long as it has a predecesing character so the `\` reverses this to searching  and matching the first `.` it finds. Key here, it matches first `.` only, this is because this character class is not greedy. A greedy character class is designated with a `+` on the right side of the character class `[]'s`. They are called greedy because they will match all available characters that match its parameters, they will match all possible characters in the given sting or, if strung together with non greedy character classes, like in this expression at `@`, at the red  `\.` above , and here at `([a-z\.]{2,6})`. Unless a character class has something after it's `[]` it only finds the first match.

## \ .{n,m}  Quantifiers
### The last non-greedy character class mentioned in the past section :`([a-z\.]{2,6})`

### has a different kind of parameter  attached `{2,6}` this is telling it to match only if there is two or more and less than six characters ('aa'-'aaaaaa'). These units can of course be swaped so long as the first number is smaller than the second. 

## Tying it all Together
### The last key needed to explain the regex expression is simply to walk through its functionality in order. To start a reminder of the main expression: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

### the expression starts at beginning boundry `/^` then has a capture group with a character class of : `([a-z0-9_\.-]+)` followed by an `@`  the first character class will return true so long as some number of lowercase letters, integers, underscores, or hyphens (as long as the hyphen isnt the first character of the string) exist before the first `@` character. If there is  anything that isn't a lowercase letter, integer, underscore, or hyphens (as long as the hyphen isnt the first character of the string) before the `@` or there is no `@` it will return false. The next capturing group : `([\da-z\.-]+)` calls for any number of lowercase letters, integers, underscores, or hyphens (as long as the hyphen isnt the first character of the string) until it is stopped by the next group : ` \.` which is looking for the first period . If the string between the `@` and the `\.` has anything besides lowercase letters, integers, underscores, or hyphens (as long as the hyphen isnt the first character of the string), or there is no `\.` it returns false the final category group `.([a-z\.]{2,6})` only accepts lowercase letters that are at least two in length but no more than six ('aa'-'aaaaaa') otherwise returns false. After that the expression is closed off with its ending boundry : `$/`
## Questions
If you have any questions about this gist please feel free to email me. 

-Email: kylec0217@gmail.com 


or checkout some of my other projects

-GitHub Username: krestle80 