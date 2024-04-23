---
tags:
  - exercise
  - begginer
---
```cs
Random rnd = new Random();

int rndNumber = rnd.Next(2);

string result = rndNumber == 0 ? "heads" : "tails";

Console.WriteLine($"The winner is {result}");
```

[[Exercise]]