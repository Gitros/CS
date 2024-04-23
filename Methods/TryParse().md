---
tags:
  - methods
---

The `TryParse()` method is a valuable tool. Here are few quick ideas to remember.

- Use `TryParse()` when converting a string into a numeric data type.
- `TryParse()` returns `true` if the conversion is successful, `false` if it's unsuccessful.
- Out parameters provide a secondary means of a method returning a value. In this case, the `out` parameter returns the converted value.
- Use the keyword `out` when passing in an argument to a method that has defined an `out` parameter.

### Example

```cs
string value = "bad";
int result = 0;
if (int.TryParse(value, out result))
{
   Console.WriteLine($"Measurement: {result}");
}
else
{
   Console.WriteLine("Unable to report the measurement.");
}

if (result > 0)
   Console.WriteLine($"Measurement (w/ offset): {50 + result}");
```

[[Methods]]
