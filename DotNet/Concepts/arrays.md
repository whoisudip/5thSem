

---

## 🔢 What Is an Array?

An **array** in C# is a **fixed-size** collection of elements of the **same type**, stored in **contiguous memory**.

---

## 📦 Types of Arrays in C\#

| Type               | Description                                   | Example                          |
| ------------------ | --------------------------------------------- | -------------------------------- |
| Single-Dimensional | Simple, one row of items                      | `int[] numbers = new int[5];`    |
| Multi-Dimensional  | Rectangular grid (like a matrix)              | `int[,] matrix = new int[2,3];`  |
| Jagged Array       | Array of arrays (rows can be different sizes) | `int[][] jagged = new int[3][];` |

---

### ✅ 1. **Single-Dimensional Array**

```csharp
int[] numbers = new int[3];
numbers[0] = 10;
numbers[1] = 20;
numbers[2] = 30;

foreach (int num in numbers)
    Console.WriteLine(num);  // 10, 20, 30
```

Or:

```csharp
int[] numbers = { 10, 20, 30 };
```

---

### ✅ 2. **Multi-Dimensional Array** (Rectangular)

```csharp
int[,] matrix = new int[2, 3] 
{
    { 1, 2, 3 },
    { 4, 5, 6 }
};

Console.WriteLine(matrix[1, 2]);  // Output: 6
```

Access with two indexes: `[row, column]`.

---

### ✅ 3. **Jagged Array** (Array of Arrays)

```csharp
int[][] jagged = new int[2][];
jagged[0] = new int[] { 1, 2 };
jagged[1] = new int[] { 3, 4, 5 };

Console.WriteLine(jagged[1][2]);  // Output: 5
```

Each row can have a different number of columns.

---

### ✅ 4. **Array Class Methods**

You can use static methods from the `System.Array` class:

```csharp
int[] nums = { 5, 2, 9, 1 };

Array.Sort(nums);        // Sorts the array
Array.Reverse(nums);     // Reverses the array
int index = Array.IndexOf(nums, 2); // Finds the index of 2
```

---

## 🎯 Bonus: Useful Array Methods & Properties

| Feature             | Example                    |
| ------------------- | -------------------------- |
| `Length`            | `array.Length`             |
| `Rank` (dimensions) | `array.Rank`               |
| `Clone()`           | `array.Clone()`            |
| `CopyTo()`          | `array.CopyTo(newArr, 0);` |

---

## 🧠 Summary

| Array Type         | Shape  | Syntax Example                   |
| ------------------ | ------ | -------------------------------- |
| Single-Dimensional | `[]`   | `int[] arr = new int[3];`        |
| Multi-Dimensional  | `[,]`  | `int[,] mat = new int[2,2];`     |
| Jagged             | `[][]` | `int[][] jagged = new int[3][];` |

---
