---
tags:
  - values
  - begginer
---

Podczas pracy z typami danych liczbowych warto określić, czy wartość jest większa lub mniejsza niż inna wartość. Użyj następujących operatorów, aby wykonać te typy porównań:

- Większe niż `>`
- Mniejsze niż `<`
- Większe niż lub równe `>=`
- Mniejsze niż lub równe `<=`

`==` Oczywiście operatory i `!=` użyte do porównywania powyższych wartości ciągów również będą działać podczas porównywania typów danych liczbowych.

Przed sprawdzeniem dwóch wartości ciągu pod kątem równości, zwłaszcza gdy jedna lub obie wartości zostały wprowadzone przez użytkownika, należy:

- Użyj metody pomocniczej `ToUpper()` lub `ToLower()` dla wartości ciągów, aby zapewnić, że oba ciągi będą zawierać wyłącznie wielkie lub małe litery.
- Usuń wszystkie wiodące lub końcowe puste spacje przy użyciu metody pomocniczej `Trim()` dla dowolnej wartości ciągu.

Poprzednie sprawdzanie równości można poprawić, łącząc te dwie metody pomocnicze w obu wartościach, jak pokazano na poniższej liście kodu:

```cs
string value1 = " a";

string value2 = "A ";

Console.WriteLine(value1.Trim().ToLower() == value2.Trim().ToLower());
```

Jak można się spodziewać, wynik użycia operatora nierówności jest przeciwieństwem tego, co zostało wyświetlone podczas korzystania z operatora równości. Oznacza to, że kod będzie również rozgałęzić się w odwrotny sposób, co może być dokładnie tym, co chcesz.

## Examples

```cs
Console.WriteLine("a" != "a");

Console.WriteLine("a" != "A");

Console.WriteLine(1 != 2);



string myValue = "a";

Console.WriteLine(myValue != "a");
```

```output
False
True
True
False
```

```cs
Console.WriteLine(1 > 2);

Console.WriteLine(1 < 2);

Console.WriteLine(1 >= 1);

Console.WriteLine(1 <= 1);
```

## Logic negation

```cs
string pangram = "The quick brown fox jumps over the lazy dog.";

Console.WriteLine(pangram.Contains("fox"));

Console.WriteLine(pangram.Contains("cow"));
```

```cs
string pangram = "The quick brown fox jumps over the lazy dog.";

Console.WriteLine(!pangram.Contains("fox"));

Console.WriteLine(!pangram.Contains("cow"));
```

```cs
int a = 7;

int b = 6;

Console.WriteLine(a != b); // true



string s1 = "Hello";

string s2 = "Hello";

Console.WriteLine(s1 != s2); // false
```

## Summary

Oto główne informacje o ocenianiu wyrażeń logicznych, które przedstawiono dotychczas:

- Istnieje wiele różnych rodzajów wyrażeń, których wynikiem jest wartość `true` lub `false`.
- Do oceniania równości służy operator `==`.
- Ocena równości ciągów wymaga rozważenia możliwości, że ciągi mają inny przypadek i spacje wiodące lub końcowe. Zależnie od sytuacji używaj metod pomocniczych `ToLower()` lub `ToUpper()` oraz metody pomocniczej `Trim()`, aby zwiększyć prawdopodobieństwo tego, że dwa ciągi są równe.
- Do oceniania nierówności służy operator `!=`.
- Do oceniania porównań „większe niż”, „mniejsze niż” i podobnych operacji służą operatory porównywania, takie jak `>`, `<`, `>=` i `<=`.
- Jeśli metoda zwraca wartość logiczną, może być używana jako wyrażenie logiczne.
- Używaj operatora negacji logicznej `!`, aby oceniać przeciwieństwo danego wyrażenia.

[[https://learn.microsoft.com/pl-pl/training/modules/csharp-evaluate-boolean-expressions/2-exercise-boolean-expressions]]

[[CS]]
