---
tags:
  - methods
---
Calling the `Resize()` method passing in the `pallets` array by reference, using the `ref` keyword. In some cases, methods require you pass arguments by value (the default) or by reference (using the ref keyword). The reasons why this is necessary requires a long and complicated explanation about of how objects are managed in .NET. Unfortunately, that is beyond the scope of this module. When in doubt, you're recommended to look at Intellisense or Microsoft Docs for examples on how to properly call a given method.

In this case, you're resizing the `pallets` array from four elements to `6`. The new elements are added at the end of the current elements. The two new elements will be null until you assign a value to them.

- Use the `Resize()` method to change the number of elements in the array, removing or adding elements from the end of the array.
- New array elements and cleared elements are null, meaning they don't point to a value in memory

```cs
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Array.Clear(pallets, 0, 2);
Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine("");
Array.Resize(ref pallets, 6);
Console.WriteLine($"Resizing 6 ... count: {pallets.Length}");

pallets[4] = "C01";
pallets[5] = "C02";

foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

[[Methods]]