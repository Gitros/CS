---
tags:
  - methods
---

- The `Remove()` method works like the `Substring()` method, except that it deletes the specified characters in the string.
- The `Replace()` method swaps all instances of a string with a new string.

### Remove()

You would typically use `Remove()` when there's a standard and consistent position of the characters you want to remove from the string.

```cs
string data = "12345John Smith          5000  3  ";
string updatedData = data.Remove(5, 20);
Console.WriteLine(updatedData);
```

```output
123455000  3
```

The `Remove()` method works similarly to the `Substring()` method. You supply a starting position and the length to remove those characters from the string.

### Replace()

The `Replace()` method is used when you need to replace one or more characters with a different character (or no character). The `Replace()` method is different from the other methods used so far, it **replaces every instance** of the given characters, not just the first or last instance.

```cs
string message = "This--is--ex-amp-le--da-ta";
message = message.Replace("--", " ");
message = message.Replace("-", "");
Console.WriteLine(message);
```

```output
This is example data
```

[[Methods]]
