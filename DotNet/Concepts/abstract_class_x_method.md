### 🔹 Abstract Class & Abstract Method in C# (.NET)

Abstract classes and methods are used to define **incomplete classes** or **shared base templates** that must be extended and implemented by derived classes. They support **inheritance** and **polymorphism**, but **cannot be instantiated directly**.

---

## 🧱 1. **Abstract Class**

An `abstract class`:

* **Cannot be instantiated**.
* Can **contain abstract methods** (without a body) and **regular methods** (with a body).
* Acts as a **base class** for other classes.

### Example:

```csharp
abstract class Animal
{
    public abstract void MakeSound();  // abstract method (no body)
    
    public void Eat()  // regular method
    {
        Console.WriteLine("Animal is eating.");
    }
}
```

---

## ⚙️ 2. **Abstract Method**

An `abstract` method:

* Has **no body**.
* Must be **overridden** in a derived class.
* Can **only exist inside an abstract class**.

### Example:

```csharp
class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}
```

---

### 🧪 Full Example:

```csharp
abstract class Animal
{
    public abstract void MakeSound();  // must be implemented by derived class

    public void Sleep()
    {
        Console.WriteLine("Animal is sleeping.");
    }
}

class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Cat meows.");
    }
}
```

### Usage:

```csharp
Animal a = new Cat();
a.MakeSound();   // Output: Cat meows.
a.Sleep();       // Output: Animal is sleeping.
```

---

## 🧠 Summary Table

| Feature             | Abstract Class         | Abstract Method                    |
| ------------------- | ---------------------- | ---------------------------------- |
| Can be instantiated | ❌ No                   | ❌ No (no body)                     |
| Purpose             | Base for derived types | Enforces method implementation     |
| Contains code       | ✅ Yes (partial)        | ❌ No (must be overridden)          |
| Modifiers used      | `abstract class`       | `abstract` keyword in class method |

---
