### 🔹 Virtual Method in C# (.NET)

A **virtual method** in C# is a method that is **declared in a base class** and is **meant to be overridden** in a derived class. It supports **runtime polymorphism**, allowing different behavior depending on the object type, even when accessed through a base class reference.

---

### ✅ Key Concepts

* **Declared using `virtual`** in the base class.
* **Overridden using `override`** in the derived class.
* Enables **dynamic dispatch** (deciding at runtime which method to execute).

---

### 📘 Example:

```csharp
class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Dog barks.");
    }
}

class Cat : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Cat meows.");
    }
}
```

### 🔁 Runtime Behavior:

```csharp
Animal animal = new Dog();
animal.Speak(); // Output: Dog barks.

animal = new Cat();
animal.Speak(); // Output: Cat meows.
```

> Even though `animal` is of type `Animal`, the **overridden method** in `Dog` or `Cat` gets executed — thanks to **virtual/override**.

---

### ⚠️ Without `virtual/override`:

If you don’t use `virtual` in the base class and `override` in the derived class, **method hiding** (not overriding) occurs using the `new` keyword.

```csharp
class Animal
{
    public void Speak() => Console.WriteLine("Animal sound.");
}

class Dog : Animal
{
    public new void Speak() => Console.WriteLine("Dog barks.");
}
```

```csharp
Animal animal = new Dog();
animal.Speak();  // Output: Animal sound. (because it's not virtual)
```

---

### 🧠 Summary

| Keyword    | Purpose                              |
| ---------- | ------------------------------------ |
| `virtual`  | Marks method for override in derived |
| `override` | Overrides a virtual method           |
| `new`      | Hides the base method (not override) |

---
