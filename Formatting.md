---
tags:
  - shortcut
---
- You can use composite formatting or string interpolation to format strings.
- With **composite formatting**, you use a string template containing one or more replacement tokens in the form `{0}`. You also supply a list of arguments that are matched with the replacement tokens based on their order. Composite formatting works when using `string.Format()` or `Console.WriteLine()`.
- With **string interpolation**, you use a string template containing the variable names you want replaced surrounded by curly braces. Use the `$` directive before the string template to indicate you want the string to be interpolated.
- Format currency using a `:C` specifier.
- Format numbers using a `:N` specifier. Control the precision (number of values after the decimal point) using a number after the `:N` like `{myNumber:N3}`.
- Format percentages using the `:P` format specifier.
- Formatting currency and numbers depend on the end user's culture, a five character code that includes the user's country/region and language (per the settings on their computer).

```cs
decimal price = 67.55m;
decimal salePrice = 59.99m;

string yourDiscount = String.Format("You saved {0:C2} off the regular {1:C2} price. ", (price - salePrice), price);

yourDiscount += $"A discount of {((price - salePrice)/price):P2}!"; //inserted
Console.WriteLine(yourDiscount);
```

```output
You saved $7.56 off the regular $67.55 price. A discount of 11.19%!
```


- Methods that add blank spaces for formatting purposes (`PadLeft()`, `PadRight()`)
- Methods that compare two strings or facilitate comparison (`Trim()`, `TrimStart()`, `TrimEnd()`, `GetHashcode()`, the `Length` property)
- Methods that help you determine what's inside of a string, or even retrieve just a part of the string (`Contains()`, `StartsWith()`, `EndsWith()`, `Substring()`)
- Methods that change the content of the string by replacing, inserting, or removing parts (`Replace()`, `Insert()`, `Remove()`)
- Methods that turn a string into an array of strings or characters (`Split()`, `ToCharArray()`)



- The `string` data type, literal strings, and variables of type string each implement many helper methods to format, modify, and perform other operations on strings.
- The `PadLeft()` and `PadRight()` methods add white space (or optionally, another character) to the total length of a string.
- Use `PadLeft()` to right-align a string.
- Some methods are overloaded, meaning they have multiple versions of the method with different arguments that affect their functionality.
- The `+=` operator concatenates a new string on the right to the existing string on the left.

[[CS]]