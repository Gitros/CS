---
tags:
  - methods
---
Separate each element of the char array using a comma, as is common when working with data that is represented as ASCII text. To do that, you'll comment out the line of code you added in Step 2 and use the `String` class' `Join()` method, passing in the char you want to delimit each segment (the comma) and the array itself.

- Use methods like `Join()`, or create a new string passing in an array of `char` to turn the array back into a single string

```cs
string value = "abc123";
char[] valueArray = value.ToCharArray();
Array.Reverse(valueArray);

string result = String.Join(",", valueArray);
Console.WriteLine(result);
```

```output
3,2,1,c,b,a
```

[[Methods]]