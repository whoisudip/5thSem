Inheritance in object-oriented programming (including **.NET/C#**) is a way for one class to acquire the **properties and behaviors (methods)** of another class. This helps in code reuse and establishing a natural hierarchy.

---

## 🔹 Types of Inheritance in .NET

### ✅ 1. **Single Inheritance**

One class inherits from one base class.

```csharp
class Animal
{
    public void Eat() => Console.WriteLine("Eating...");
}

class Dog : Animal
{
    public void Bark() => Console.WriteLine("Barking...");
}
```

---

### ✅ 2. **Multilevel Inheritance**

A class inherits from a class that itself inherits from another class.

```csharp
class Animal
{
    public void Eat() => Console.WriteLine("Eating...");
}

class Mammal : Animal
{
    public void Walk() => Console.WriteLine("Walking...");
}

class Dog : Mammal
{
    public void Bark() => Console.WriteLine("Barking...");
}
```

> 🔸 Here, `Dog` indirectly inherits from `Animal` through `Mammal`.

---

### 🚫 3. **Multiple Inheritance (Not Supported for Classes in C#)**

C# **does not support multiple class inheritance** directly (i.e., a class cannot inherit from more than one class).

```csharp
// ❌ This is illegal in C#
class A { }
class B { }
class C : A, B { }  // Not allowed
```

---

### ✅ Multiple Inheritance via Interfaces (Supported)

C# allows **multiple interface inheritance**, which is a common and powerful alternative.

```csharp
interface IWalk
{
    void Walk();
}

interface IBark
{
    void Bark();
}

class Dog : IWalk, IBark
{
    public void Walk() => Console.WriteLine("Walking...");
    public void Bark() => Console.WriteLine("Barking...");
}
```

> ✔️ This allows C# to achieve **multiple inheritance of behavior** without the complexity of multiple base classes.

---

### Summary Table:

| Type                  | Supported in C# | Example Form       |
| --------------------- | --------------- | ------------------ |
| Single Inheritance    | ✅ Yes           | `class B : A`      |
| Multilevel            | ✅ Yes           | `C : B`, `B : A`   |
| Multiple (Classes)    | ❌ No            | `class C : A, B` ❌ |
| Multiple (Interfaces) | ✅ Yes           | `class C : IA, IB` |

---
