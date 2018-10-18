# CSV <3 Numerics Format

_CSV Records with Auto-Converted Numerics (Float Numbers) Encoding Rules - A Modern (Simple) Tabular Data Format incl. Numbers, Comments and More_



## "Classic" Comma-Separated Values (CSV) - Strings, String, Strings. Always. Period.

Let's read:

```
1,2,3
"4","5","6"
```

What do you expect? In the "classic" vanilla format
the comma-separated values once read in / parsed
always are a list of string values. Period.

``` yaml
[["1", "2", "3"],
 ["4", "5", "6"]]
```


## What about Numbers (and Strings Together)? - How? Possible?

Guess, what? There's a popular comma-separated values (CSV)
convention / variant / dialect
that now has an official specification:

Rule 1: Use "un-quoted" values for float numbers e.g. `1,2,3` or `1.0, 2.0, 3.0` etc.

Rule 2: Use quoted values for "non-numeric" strings e.g. `"4", "5", "6"` or `"Hello, World!"` etc.


Example:

```
1,2,3
"4","5","6"
```

returns / maps to

``` yaml
[[1.0, 2.0, 3.0],
 ["4", "5", "6"]]
```

and now has an official name. Let's call it:

CSV <3 Numerics  or  CSV ❤ Numerics




## What about Not A Number (NaN)?

A CSV <3 Numberics reader / parser also lets you configure a list of values
that get auto-converted to `NaN`, that is, Not A Number (NaN).
Example:

```
1,2,NAN,#NAN
```

with the nan option ` ['NAN', '#NAN']`
returns / maps to:

``` yaml
[[1.0, 2.0, NaN, NaN]]
```

Note: The Not a Number (NaN) values are "un-quoted" values (like numbers)
in the comma-separated values (CSV) format.



## What about Comments and Blank Lines and Leading and Trailings (White)spaces?

Yes, in CSV <3 Numberics you can use comments (starting with `#`) and blank lines
and leading and trailing (white)spaces - they all will get skipped and trimmed automatically.
Example:

``` 
# CSV <3 Numerics

 1  ,   2   ,   3
"4" ,  "5"  ,  "6"
```

returns / maps to

``` yaml
[[1.0, 2.0, 3.0],
 ["4", "5", "6"]]
```







