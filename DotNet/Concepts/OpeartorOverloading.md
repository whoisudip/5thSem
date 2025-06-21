

---

# 🔹 Operator Overloading in C\#

Operator overloading lets you **define custom behavior** for operators (`+`, `-`, `==`, etc.) when applied to instances of your classes or structs.

---

## ⚙️ Why Overload Operators?

* Make your custom types behave like built-in types.
* Write clean, intuitive code.
* Improve readability when performing operations on your objects.

---

## 📌 Rules for Operator Overloading

* You **must** declare operator overloads as `public static` methods inside the class or struct.
* At least **one operand must be your user-defined type**.
* You **cannot create new operators**; you can only overload existing ones.
* Some operators **must be overloaded in pairs**, like `==` and `!=`.

---

## 1️⃣ Binary Operator Overloading

Binary operators work with **two operands**.

**Example: Overload `+` operator for a `Complex` number class**

```csharp
public class Complex
{
    public double Real { get; }
    public double Imaginary { get; }

    public Complex(double r, double i)
    {
        Real = r;
        Imaginary = i;
    }

    // Overload + operator
    public static Complex operator +(Complex c1, Complex c2)
    {
        return new Complex(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);
    }

    public override string ToString() => $"{Real} + {Imaginary}i";
}
```

**Usage:**

```csharp
var c1 = new Complex(1.5, 2.5);
var c2 = new Complex(3.0, 4.0);
var sum = c1 + c2;
Console.WriteLine(sum);  // Output: 4.5 + 6.5i
```

---

## 2️⃣ Unary Operator Overloading

Unary operators operate on **one operand**. Examples: `-`, `!`, `++`, `--`

**Example: Overload unary `-` operator for `Complex`**

```csharp
public static Complex operator -(Complex c)
{
    return new Complex(-c.Real, -c.Imaginary);
}
```

---

## 3️⃣ Relational Operator Overloading

Relational operators compare two objects: `==`, `!=`, `<`, `>`, `<=`, `>=`.

* **Important:** If you overload `==`, you **must also overload** `!=`.
* Usually, these operators should be consistent with `Equals()` and `GetHashCode()`.

---

**Example: Overload `==` and `!=` for `Complex`**

```csharp
public static bool operator ==(Complex c1, Complex c2)
{
    // Handle nulls and compare properties
    if (ReferenceEquals(c1, c2)) return true;
    if (ReferenceEquals(c1, null) || ReferenceEquals(c2, null)) return false;

    return c1.Real == c2.Real && c1.Imaginary == c2.Imaginary;
}

public static bool operator !=(Complex c1, Complex c2) => !(c1 == c2);

public override bool Equals(object obj)
{
    if (obj is Complex other)
    {
        return this == other;
    }
    return false;
}

public override int GetHashCode() => (Real, Imaginary).GetHashCode();
```

---

## 4️⃣ Overloading Other Relational Operators

You can overload `<`, `>`, `<=`, and `>=` similarly:

```csharp
public static bool operator <(Complex c1, Complex c2)
{
    double mag1 = Math.Sqrt(c1.Real * c1.Real + c1.Imaginary * c1.Imaginary);
    double mag2 = Math.Sqrt(c2.Real * c2.Real + c2.Imaginary * c2.Imaginary);
    return mag1 < mag2;
}

public static bool operator >(Complex c1, Complex c2) => !(c1 < c2) && c1 != c2;

public static bool operator <=(Complex c1, Complex c2) => (c1 < c2) || (c1 == c2);

public static bool operator >=(Complex c1, Complex c2) => (c1 > c2) || (c1 == c2);
```

---

## Summary Table

| Operator Type | Signature Example                          | Notes                                |    |
| ------------- | ------------------------------------------ | ------------------------------------ | -- |
| Binary        | `public static T operator +(T a, T b)`     | `+`, `-`, `*`, `/`, `%`, `&`, \`     | \` |
| Unary         | `public static T operator -(T a)`          | `-`, `!`, `++`, `--`                 |    |
| Equality      | `public static bool operator ==(T a, T b)` | Must also overload `!=`              |    |
| Inequality    | `public static bool operator !=(T a, T b)` |                                      |    |
| Relational    | `public static bool operator <(T a, T b)`  | Must overload `<` and `>` together   |    |
| Relational    | `public static bool operator >(T a, T b)`  |                                      |    |
| Relational    | `public static bool operator <=(T a, T b)` | Must overload `<=` and `>=` together |    |
| Relational    | `public static bool operator >=(T a, T b)` |                                      |    |

---

## Important Notes

* **Operator overloading should be intuitive and follow expected semantics**; confusing overloads make code hard to maintain.
* Avoid overloading operators in ways that confuse users.
* **Always override `Equals()` and `GetHashCode()`** when overloading `==` and `!=`.

---
