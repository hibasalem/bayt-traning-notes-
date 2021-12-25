# regex

### ways to creat

-let something = new RegExp("something")
-let something = /something/;

### methods

- `regex.test(txt)` , return true false
- `regex.exac(txt)`, return array of the matches and there indexs
- `txt.match(regex)` , same as exac
- `txt.serch(regex)` , return index
- `txt.replace(regex , "txt to add")` ,return a new srting with the regex replaced with the other text
- there is toString and split also

### modifiers (flags)

`/pattern/flag;`

- g , all matches
- i , case insensitive
- m , maltiline match , it affect the `^` and `$`
- s , dotall , This flag can be added to your regular expression if you would like the wildcard character to match all characters.

### metacharacters

- `^` , excluding a characters set "not" , also as first of line anchore,
- `$` , match at end of line
- `.` wildcard , means any thing single characters `/h.t/` match hat hot...ect
- `*` zero or more occurrences
- `+` one or more occurrences
- `?` zero or one occurrences
- `=`
- `!`
- `:`
- `|`
- `\`
- `/`
- `(`
- `)`
- `[`
- `]`
- `{`
- `}`

escaping metacharacters `\`

### control characters

- `\t` , tab
- `\v` , virtical tab
- `\n` , newlin
- `\r` , carriage return

### characters set

`[things]` , get one of the group of characters

- it can be litterals where we add them all
- `[1-4] [a-z] [1-6a-z]` , ranges
- shorthands
  - `\d` , [1-9]
  - `\w` , word [a-zA-Z0-9_]
  - `\s` , white space [\r\n\t]
  - `\D` , [^0-9]
  - `\W` , [^a-za-z0-9_]
  - `\S` , [^\r\n\t]

### characters repitition

`+` `?` `*`

- `*` zero or more occurrences (of the character to the left) , greediness
- `+` one or more occurrences
- `?` zero or one occurrences , laziness

- specifying repitition amount `{min,max}` between the two numbers

### anchored expresstions

to define the position

- `^` start of the line
- `$` end of the line

the m flag , maltiline match (it make it work when we have enter .... )

- word boundaries
  - `\b` word boundary
  - `\B` nonword boundary

### alternates

- `|`like or

### grouping

- `()` , examples we would use it with repitting `([a-z][1-9]){5}` or word bounderies `\b(ssjofjs | sljflksjf | jsfisjf)\b`

- group capture text , we can make it noncapturing group by adding `?:` in the start of the group `(?:.....)`
- we can refrance the captured group , that would capture the acctual text that matched not the pattren
- we can name it like this `(?<name>)` , we would refrreance that by `\k<name>`

- **_Lookahead Groups_** , it matches it but doesnt capture it , `(?=things)` , it doesnt count characters , use example , passwords
- **_Negative Lookahead Groups_**  , `(?=!things)` , make sure that it doesnt include something
- ***Lookbehind Groups*** , ????


