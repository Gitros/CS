---
tags:
  - methods
---
Using the `Sort()` method of the `Array` class to sort the items in the array alphanumerically.

- Use the `Sort()` method to manipulate the order based on the given data type of the array.

```cs
string[] pallets = { "B14", "A11", "B12", "A13" };

Console.WriteLine("Sorted...");
Array.Sort(pallets);
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
```

[[Methods]]