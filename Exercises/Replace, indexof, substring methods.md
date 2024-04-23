---
tags:
  - exercise
  - methods
---
```cs
const string input = "<div><h2>Widgets &trade;</h2><span>5000</span></div>";
string quantity = "";
string output = "";

//quantity

const string openSpan = "<span>";
const string closeSpan = "</span>";

int openingSpan = input.IndexOf(openSpan) + openSpan.Length;
int closingSpan = input.IndexOf(closeSpan);
int spanLength = closingSpan - openingSpan;

quantity = input.Substring(openingSpan, spanLength);
quantity = $"Quantity: {quantity}";

// output

const string openDiv = "<div>";
const string closeDiv = "</div>";

int openingDiv = input.IndexOf(openDiv);
int closingDiv = input.IndexOf(closeDiv);
openingDiv += openDiv.Length;
int sentenceLength = closingDiv - openingDiv;

output = input.Substring(openingDiv, sentenceLength);
output = output.Replace("&trade", "&reg");
output = $"Output: {output}";

Console.WriteLine(quantity);
Console.WriteLine(output);
```

```output
5000
<h2>Widgets &reg;</h2><span>5000</span>
```

[[Exercise]]