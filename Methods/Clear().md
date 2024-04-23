---
tags:
  - methods
---
The `Array.Clear()` method allows you to remove the contents of specific elements in your array and replace it with the array default value. For example, in a `string` array the element value cleared is replaced with `null`, when you clear a `int` array element the replacement is done with `0` (zero).

- Use the `Clear()` method to empty the values out of elements in the array.
- New array elements and cleared elements are null, meaning they don't point to a value in memory.
### Example

```cs
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Array.Clear(pallets, 0, 2);
Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```
Here using the `Array.Clear()` method to clear the values stored in the elements of the `pallets` array starting at index `0` and clearing `2` elements.

```output
Clearing 2 ... count: 4
-- 
-- 
-- B12
-- A13
```

## Empty string versus null

When you use `Array.Clear()`, the elements that were cleared no longer reference a string in memory. In fact, the element points to nothing at all. pointing to nothing is an important concept that can be difficult to grasp at first.

What if you attempt to retrieve the value of an element that was affected by the `Array.Clear()` method, could you do it?

### Access the value of a cleared element

```cs
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Console.WriteLine($"Before: {pallets[0]}");
Array.Clear(pallets, 0, 2);
Console.WriteLine($"After: {pallets[0]}");

Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

#### Output:
```output
Before: B14
After:
Clearing 2 ... count: 4
--
--
-- B12
-- A13
```

[[Methods]]