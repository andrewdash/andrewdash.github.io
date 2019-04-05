Regex is an incredibly useful tool for looking through text. It's essentially like using CTRL-f, but now you can get those outputs stored into one spot as you desire. The following will be regex using python.

- Want to pull all of the phone numbers in a 50-page doc?
- want to pull phone numbers & emails from your clipboard?

Use regex.


#### Getting Started
The package __re__ is use for python's regex. Make sure to run __import re__ to be able to use it in the program.

Check out the following code:
```python3
phoneNumRegex = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')
mo = phoneNumRegex.search('My number is 415-555-4242.')
print('Phone number found: ' + mo.group())
Phone number found: 415-555-4242
```

Once you define your regex pattern (in `.compile`), you run `search()` on it with the text you want to look through. `search()` will return None if the regex pattern isn't found in the string. `group()` outputs the matched text.

#### Grouping with Parentheses
In your regex pattern, you can create different __groups__ by putting __()__ around them.
```
>>> phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d-\d\d\d\d)')
>>> mo = phoneNumRegex.search('My number is 415-555-4242.')
>>> mo.group(1)
'415'
>>> mo.group(2)
'555-4242'
>>> mo.group(0)
'415-555-4242'
>>> mo.group()
'415-555-4242'

If you would like to retrieve all the groups at once, use the groups() method—note the plural form for the name.

>>> mo.groups()
('415', '555-4242')
```
#### Using findall()
`search()` returns the first matched text found, but `findall()` returns a list of all matches found, as long as there are no groups in the regular expression!!
- `search()` returns a Match() object, while `findall()` returns a list object; if `findall()` does have groups, it'll return a list of tuples



#### Regex OR, using pipe symbol --> |
```>>> batRegex = re.compile(r'Bat(man|mobile|copter|bat)')
>>> mo = batRegex.search('Batmobile lost a wheel')
>>> mo.group()
'Batmobile'
>>> mo.group(1)
'mobile'
```

#### More Regex symbols
- __?__ --> Bat(wo)?man --> the wo is optionally matched (0 or 1)
- __*__ --> Bat(wo)\*man -->  the wo is matched with ZERO or more (optional, or one, or many)
- __+__ --> Bat(wo)+man --> the wo is matched with ONE or more (at least one)
- __{}__ --> (Ha){2,4} --> match HaHa, HaHaHa, or HaHaHaHa (you can also do { , 2}, which would be "zero to two"; or {3, }, which would be "3 and more than that"; or {2}, which would be "exactly two")

#### Greedy & Non-greedy matching
Python by default is greedy matching, which means it chooses the longest string possible. __Non-greedy matches to the shortest string possible__.
```
>>> greedyHaRegex = re.compile(r'(Ha){3,5}')
>>> mo1 = greedyHaRegex.search('HaHaHaHaHa')
>>> mo1.group()
'HaHaHaHaHa'

>>> nongreedyHaRegex = re.compile(r'(Ha){3,5}?')
>>> mo2 = nongreedyHaRegex.search('HaHaHaHaHa')
>>> mo2.group()
'HaHaHa'
```

#### Caret and Dollar Sign and Bracket characters
Caret can be used for 2 situations
- __^__ --> caret character (^) is the NOT operator. `r'[^aeiouAEIOU]` means give me all characters that are NOT vowels
- __^__ --> caret character (^) at the start of the regex pattern means the match must occur at the beginning of the searched text. (example: `r'Hello` will look for Hello at the beginning of the text you input)
- __$__ --> dollar sign tells you that the string must end with that regex pattern
  examples:
    - `r'\d$` = string must end with a digit
    - `r'^\d+$` = string must have only one or more digits
- __[]__ --> brackets let you create custom character classes. Escape characters are read literally, so [0-5\.] will read the backslash and dot literally.

#### wild card character (the dot)
- The . (the dot) will match any one character that isn't a new line.
- Since . means any one character and * means zero or more, combining them into __.*__ means match anything

greedy & nongreedy versions of using the dot
```
>>> nongreedyRegex = re.compile(r'<.*?>')
>>> mo = nongreedyRegex.search('<To serve man> for dinner.>')
>>> mo.group()
'<To serve man>'

>>> greedyRegex = re.compile(r'<.*>')
>>> mo = greedyRegex.search('<To serve man> for dinner.>')
>>> mo.group()
'<To serve man> for dinner.>'
```

#### How can I match all text that has new line in it?
The . or .* won't match new lines (`\n`), so in order to include new lines, you need to use re.DOTALL

```
>>> noNewlineRegex = re.compile('.*')
>>> noNewlineRegex.search('Serve the public trust.\nProtect the innocent.
\nUphold the law.').group()
'Serve the public trust.'

>>> newlineRegex = re.compile('.*', re.DOTALL)
>>> newlineRegex.search('Serve the public trust.\nProtect the innocent.
\nUphold the law.').group()
'Serve the public trust.\nProtect the innocent.\nUphold the law.'
```

#### Need to make really complex regex? Enter re.VERBOSE argument

```
Now instead of a hard-to-read regular expression like this:

phoneRegex = re.compile(r'((\d{3}|\(\d{3}\))?(\s|-|\.)?\d{3}(\s|-|\.)\d{4}
(\s*(ext|x|ext.)\s*\d{2,5})?)')
you can spread the regular expression over multiple lines with comments like this:

phoneRegex = re.compile(r'''(
    (\d{3}|\(\d{3}\))?            # area code
    (\s|-|\.)?                    # separator
    \d{3}                         # first 3 digits
    (\s|-|\.)                     # separator
    \d{4}                         # last 4 digits
    (\s*(ext|x|ext.)\s*\d{2,5})?  # extension
    )''', re.VERBOSE)
```
