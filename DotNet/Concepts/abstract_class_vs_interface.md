
---

## 🧩 Abstract Class vs Interface in C\#

| Feature                  | **Abstract Class**                | **Interface**                              |
| ------------------------ | --------------------------------- | ------------------------------------------ |
| Can contain fields       | ✅ Yes                             | ❌ No                                       |
| Can contain constructors | ✅ Yes                             | ❌ No                                       |
| Contains method bodies   | ✅ (some methods can have bodies)  | ✅ (default interface methods from C# 8.0+) |
| Can be inherited from    | ✅ One abstract class              | ✅ Multiple interfaces                      |
| Inheritance syntax       | `: BaseClass`                     | `: IInterface1, IInterface2`               |
| Use case                 | Base class with shared code       | Contract with no implementation (mostly)   |
| Object instantiation     | ❌ Cannot be instantiated directly | ❌ Cannot be instantiated                   |

---

### ✅ Example Scenario

Let’s say you’re modeling animals:

```csharp
// Abstract class provides a shared base structure
abstract class Animal
{
    public string Name;
    public abstract void MakeSound();
    public void Sleep() => Console.WriteLine("Sleeping...");
}

// Interface defines capabilities
interface IFlyable
{
    void Fly();
}
```

```csharp
class Bird : Animal, IFlyable
{
    public override void MakeSound() => Console.WriteLine("Tweet!");
    public void Fly() => Console.WriteLine("Flying...");
}
```

---

### 🧠 When to Use What?

* Use an **abstract class** when:

  * You need to share **code logic** among several related classes.
  * You want to define a **base structure** with some common functionality.

* Use an **interface** when:

  * You want to define a **contract** that multiple unrelated classes can implement.
  * You need **multiple inheritance** of behavior (C# allows multiple interfaces).

---
