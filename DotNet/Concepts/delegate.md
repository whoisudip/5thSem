### 🔹 Delegate in C# (.NET)

A **delegate** in C# is like a **pointer to a method**. It lets you store a reference to **a method with a specific signature**, and call it indirectly. Delegates are **type-safe**, **object-oriented**, and the foundation of **events** in .NET.

---

## 🧠 Why Use Delegates?

* To **call methods dynamically** at runtime.
* To **pass methods as parameters** (like function pointers).
* To implement **callback methods**.
* To define **events** and **anonymous methods** (like lambdas).

---

## ✅ Delegate Syntax

### 1. **Declare a Delegate**

```csharp
public delegate void MyDelegate(string message);
```

### 2. **Create Methods Matching the Signature**

```csharp
public class Messenger
{
    public static void SayHello(string msg) => Console.WriteLine("Hello: " + msg);
    public static void SayBye(string msg) => Console.WriteLine("Bye: " + msg);
}
```

### 3. **Use the Delegate**

```csharp
class Program
{
    static void Main()
    {
        MyDelegate del = Messenger.SayHello;
        del("John");  // Output: Hello: John

        del = Messenger.SayBye;
        del("John");  // Output: Bye: John
    }
}
```

---

## ✳️ Multicast Delegates

You can combine multiple methods in a delegate using `+` or `+=`.

```csharp
MyDelegate del = Messenger.SayHello;
del += Messenger.SayBye;

del("Sam");
// Output:
// Hello: Sam
// Bye: Sam
```

---

## 🧩 Delegate Types

| Type            | Description                             | Example                               |
| --------------- | --------------------------------------- | ------------------------------------- |
| **Single-cast** | Points to one method                    | `MyDelegate d = MethodA;`             |
| **Multicast**   | Points to multiple methods (chain)      | `d += MethodB;`                       |
| **Func<>**      | Returns a value (shortcut for delegate) | `Func<int, int> square = x => x*x;`   |
| **Action<>**    | Returns void                            | `Action<string> greet = name => ...`  |
| **Predicate<>** | Returns bool                            | `Predicate<int> isEven = x => x%2==0` |

---

## 🔁 Delegate vs Interface (Quick View)

| Feature     | Delegate            | Interface                    |
| ----------- | ------------------- | ---------------------------- |
| Represents  | A method            | A contract (set of methods)  |
| Used for    | Callbacks, events   | Inheritance and polymorphism |
| Flexibility | High (method-level) | Medium (type-level)          |

---
