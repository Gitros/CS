---
tags:
  - begginer
  - operator
---

## Co to jest operator warunkowy?

Operator `?:` warunkowy oblicza wyrażenie logiczne i zwraca jedną z dwóch wyników w zależności od tego, czy wyrażenie warunkowe daje w wyniku wartość true, czy false. *Operator* warunkowy jest często określany jakoternary operator warunkowy.

Oto podstawowa forma:

```cs
<evaluate this condition> ? <if condition is true, return this value> : <if condition is false, return this value>
```

```cs
int saleAmount = 1001;
int discount = saleAmount > 1000 ? 100 : 50;
Console.WriteLine($"Discount: {discount}");
```

### Używanie operatora warunkowego w tekście

Ten kod można jeszcze bardziej skompaktować, eliminując zmienną `discount`tymczasową.

```cs
int saleAmount = 1001;
// int discount = saleAmount > 1000 ? 100 : 50;

Console.WriteLine($"Discount: {(saleAmount > 1000 ? 100 : 50)}");
```

## Podsumowanie

Należy pamiętać następujące fakty dotyczące operatora warunkowego:

- Możesz użyć operatora warunkowego, aby zmniejszyć rozmiar kodu, ale upewnij się, że wynikowy kod jest łatwo czytelny.
- Operator warunkowy można użyć, gdy musisz zwrócić wartość opartą na warunku binarnym. Kod zwróci pierwszą opcję, gdy warunek zwróci wartość true i zwróci drugą opcję, gdy warunek zwróci wartość false.

[[Operators]]
