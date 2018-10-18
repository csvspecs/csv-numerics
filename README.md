# CSV <3 Numerics Format

_CSV Records with Auto-Converted Numerics (Float Numbers) Encoding Rules - A Modern (Simple) Tabular Data Format incl. Numbers, Comments and More_



## What about Numerics and Comma-Separated Values (CSV)?

Let's read `data.csv`:

```
1,2,3
"4","5","6"
```

What do you expect?

``` ruby
pp CSV.read( 'data.csv' )
```

returns

``` ruby
[["1", "2", "3"],
 ["4", "5", "6"]]
```

That's great.  At it's most basic
a comma-separated values record once read in / parsed
is always a list of string values. Period.




## Numbers and Strings Together - How? Possible?

Guess, what? There's a popular comma-separated values (CSV)
convention / variant / dialect
that now has an official specification:

Rule 1: Use "un-quoted" values for float numbers e.g. `1,2,3` or `1.0, 2.0, 3.0` etc.

Rule 2: Use quoted values for "non-numeric" strings e.g. `"4", "5", "6"` or `"Hello, World!"` etc.


``` ruby
pp CSV.nummeric.read( 'data.csv' )   # or CSV.num.read or CSV.n.read
```

returns

``` ruby
[[1.0, 2.0, 3.0],
 ["4", "5", "6"]]
```


and now has an official name. Let's call it:

CSV <3 Numerics  or  CSV ❤ Numerics




## What about Not A Number (NaN)?

A CSV <3 Numberics reader / parser also lets you configure a list of values
that get auto-converted to `NaN`, that is, Not A Number (NaN).
Example:

``` ruby
records = Csv.numeric.parse( '1,2,NAN,#NAN', nan: ['NAN', '#NAN'] )
pp records
# => [[1.0, 2.0, NaN, NaN]]
```

Note: The Not a Number (NaN) values are "un-quoted" values (like numbers)
in the comma-separated values (CSV) format.







