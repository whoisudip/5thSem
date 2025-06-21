### 🔹 Lambda Expressions in C# (.NET)

A **lambda expression** is a **concise way to write anonymous methods** in C#. It’s a powerful tool often used with delegates, LINQ, events, and functional programming features.

---

## ✅ Basic Syntax

```csharp
(parameters) => expression_or_block
```

* The `=>` symbol is called the **lambda operator**.
* Left side: parameters
* Right side: code (an expression or block)

---

### 🧪 Examples

```csharp
Func<int, int> square = x => x * x;
Console.WriteLine(square(5));  // Output: 25
```

```csharp
Action<string> greet = name => Console.WriteLine($"Hello, {name}!");
greet("Alice");  // Output: Hello, Alice!
```

```csharp
Predicate<int> isEven = n => n % 2 == 0;
Console.WriteLine(isEven(4));  // Output: True
```

---

## ✳️ With LINQ (Very Common Use)

```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0);

foreach (var n in evenNumbers)
    Console.WriteLine(n);  // Output: 2, 4
```

---

## 🧠 Lambda Expression vs Anonymous Method

| Feature       | Lambda Expression      | Anonymous Method        |
| ------------- | ---------------------- | ----------------------- |
| Syntax        | Short, clean (`=>`)    | Uses `delegate` keyword |
| Introduced in | C# 3.0                 | C# 2.0                  |
| Readability   | High (for small logic) | Verbose                 |

### Anonymous method example:

```csharp
Func<int, int> doubleIt = delegate(int x) { return x * 2; };
```

---

## 🧩 Lambda with Multiple Parameters and Statements

```csharp
Func<int, int, int> add = (a, b) => a + b;

Func<int, int, int> multiply = (x, y) =>
{
    Console.WriteLine("Multiplying...");
    return x * y;
};
```

---

## ✅ When to Use Lambdas

* LINQ queries
* Event handlers
* Short, inline logic
* Passing logic as parameters to methods

---


