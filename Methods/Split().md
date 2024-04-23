---
tags:
  - methods
---
`Split()` method is for variables of type `string` to create an array of strings.

- Use methods like `ToCharArray()` and `Split()` to create an array

```cs
string[] items = result.Split(',');
foreach (string item in items)
{
    Console.WriteLine(item);
}
```

```output
3 
2 
1 
c 
b 
a
```

The comma is supplied to `.Split()` as the delimiter to split one long string into smaller strings. The code then uses a `foreach` loop to iterate through each element of the newly created array of strings, `items`.

[[Methods]]