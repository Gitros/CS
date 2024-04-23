---
tags:
  - methods
---
Using the `Reverse()` method of the `Array` class to reverse the order of items

- Use the `Reverse()` method to flip the order of the elements in the array.

```cs
string[] pallets = { "B14", "A11", "B12", "A13" };

Console.WriteLine("Sorted...");
Array.Sort(pallets);
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine("");
Console.WriteLine("Reversed...");
Array.Reverse(pallets);
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

```output
Sorted...
-- A11
-- A13
-- B12
-- B14

Reversed...
-- B14
-- B12
-- A13
-- A11
```

[[Methods]]