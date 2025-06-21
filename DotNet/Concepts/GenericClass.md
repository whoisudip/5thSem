### 🔹 Generic Class in C# (.NET)

A **generic class** allows you to write **a class that works with any data type**, while maintaining **type safety**. It helps you avoid code duplication and enables reuse across many types.

---

## ✅ Syntax of a Generic Class

```csharp
class Box<T>
{
    private T content;

    public void Add(T item)
    {
        content = item;
    }

    public T Get()
    {
        return content;
    }
}
```

Here, `T` is a **type parameter**. When you create an object of this class, you specify the actual type:

```csharp
Box<int> intBox = new Box<int>();
intBox.Add(100);
Console.WriteLine(intBox.Get());  // Output: 100

Box<string> strBox = new Box<string>();
strBox.Add("Hello");
Console.WriteLine(strBox.Get());  // Output: Hello
```

---

## 🧩 Why Use Generics?

* **Type-safe**: You catch errors at compile time, not runtime.
* **Reusable**: Works with any type, no need to rewrite.
* **Performance**: Avoids boxing/unboxing for value types.
* **Cleaner code**: Eliminates the need for casting.

---

## 🔧 Common Generic Collections (from .NET)

| Type                      | Description               |
| ------------------------- | ------------------------- |
| `List<T>`                 | Dynamic array of any type |
| `Dictionary<TKey,TValue>` | Key-value pairs           |
| `Queue<T>`                | FIFO collection           |
| `Stack<T>`                | LIFO collection           |

### Example:

```csharp
List<string> names = new List<string>();
names.Add("Alice");
names.Add("Bob");
```

---

## 🎛️ Generic Class with Constraints

You can **limit** the types that can be used with a generic class using constraints:

```csharp
class Repository<T> where T : class
{
    public void Save(T entity)
    {
        Console.WriteLine($"{entity} saved.");
    }
}
```

Common constraints:

* `where T : class` – reference type only
* `where T : struct` – value type only
* `where T : new()` – must have a public parameterless constructor
* `where T : BaseClass` – must inherit from a specific class
* `where T : IInterface` – must implement a specific interface

---

## 🧠 Summary

| Feature       | Description                             |
| ------------- | --------------------------------------- |
| `T`           | Type parameter                          |
| Generic class | Works with any type                     |
| Type-safe     | Avoids casting and runtime errors       |
| Reusable      | Eliminates duplicate code for each type |

---
