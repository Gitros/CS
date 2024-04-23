---
tags:
  - methods
---

- `IndexOf()` gives you the first position of a character or string inside of another string.
- `IndexOf()` returns `-1` if it can't find a match.
- `Substring()` returns just the specified portion of a string, using a starting position and optional length.
- There's often more than one way to solve a problem. You used two separate techniques to find all instances of a given character or string.
- Avoid hardcoded **magic values**. Instead, define a `const` variable. A constant variable's value can't be changed after initialization.

```cs
string message = "What is the value <span>between the tags</span>?";

const string openSpan = "<span>";
const string closeSpan = "</span>";

int openingPosition = message.IndexOf(openSpan);
int closingPosition = message.IndexOf(closeSpan);

openingPosition += openSpan.Length;
int length = closingPosition - openingPosition;
Console.WriteLine(message.Substring(openingPosition, length));
```

[[Methods]]
