
## **1. .NET Framework and CLR**

### **1.1 What is managed code? Give reason to justify the statement "DOT NET framework is platform independent and Language interoperability".**
Managed code is code that runs under the control of the Common Language Runtime (CLR). The CLR handles things like memory management and security for the code.

- **Platform Independent:** .NET works on different operating systems (like Windows or Linux) because the CLR can run the same code anywhere it’s supported.
- **Language Interoperability:** Different languages (like C# and VB.NET) can work together because they all turn into the same Intermediate Language (IL) that the CLR understands.

---

### **1.2 What do you mean by "safe" programming language? Explain any four applied technologies in DotNet framework.**
A "safe" programming language prevents errors like memory leaks by managing things automatically. 

Four technologies in .NET:
1. **CLR:** Runs and manages the code.
2. **Garbage Collection:** Frees up memory when it’s not needed.
3. **JIT Compilation:** Turns IL into machine code for faster running.
4. **Exception Handling:** Catches and fixes errors during runtime.

---

### **1.3 What is CLR? List and explain the feature of CLR.**
CLR (Common Language Runtime) is the part of .NET that runs and manages code.

Features:
- **Garbage Collection:** Cleans up unused memory.
- **Type Safety:** Makes sure data types are used correctly.
- **Exception Handling:** Deals with errors smoothly.
- **Security:** Keeps code safe from harmful actions.

---

### **1.4 Explain overview of Microsoft .NET framework and its components in detail.**
The .NET framework helps build and run apps. It has tools and libraries to make coding easier.

Components:
- **CLR:** Runs the code and manages it.
- **Base Class Library (BCL):** Ready-made code for common tasks.
- **ASP.NET:** For web apps.
- **Windows Forms:** For desktop apps.
- **ADO.NET:** For connecting to databases.

---

### **1.5 What is the importance of Garbage collection in .NET framework? Explain .NET framework architecture with suitable diagram.**
Garbage collection automatically frees memory when objects aren’t used anymore. This stops memory leaks and makes coding simpler.

**Architecture:**
- **Languages:** Like C# or VB.NET.
- **Compilers:** Turn code into IL.
- **CLR:** Runs the IL and manages it.
- **BCL:** Provides reusable code.

*(In an exam, draw a stack: Languages → Compilers → CLR → BCL.)*

---

## **2. C# Language Basics**

### **2.1 What is optional parameter? Write a C# program which stores values in two enumerations, Department and College. It uses two functions to display the data contained in Department and College enumerations.**
An optional parameter has a default value, so you don’t need to pass it when calling a method.

```csharp
enum Department { HR, IT }
enum College { Arts, Science }

class Program {
    static void ShowDept(Department d = Department.HR) {
        Console.WriteLine(d);
    }
    static void ShowCollege(College c = College.Arts) {
        Console.WriteLine(c);
    }
    static void Main() {
        ShowDept();         // Prints HR
        ShowCollege(College.Science); // Prints Science
    }
}
```

---

### **2.2 What is difference between value type and reference type in C#? Explain the concept of boxing and unboxing with suitable program.**
- **Value Type:** Stores the actual data (e.g., `int`). Lives on the stack.
- **Reference Type:** Stores a reference to data (e.g., `string`). Lives on the heap.

**Boxing:** Turning a value type into a reference type.  
**Unboxing:** Turning it back.

```csharp
int x = 5;         // Value type
object o = x;      // Boxing
int y = (int)o;    // Unboxing
```

---

### **2.3 List any five canonical keywords in C#. Write a C# program to initialize and display array element with sum of each power.**
Five keywords: `int`, `if`, `for`, `class`, `string`.

```csharp
class Program {
    static void Main() {
        int[] arr = { 2, 3, 4 };
        for (int i = 0; i < arr.Length; i++) {
            int power = arr[i] * arr[i];
            Console.WriteLine($"Element: {arr[i]}, Power: {power}");
        }
    }
}
```

---

### **2.4 What is string interpolation? How passing argument by value is differing from passing argument by reference? Explain with program.**
String interpolation uses `{}` to put values directly in a string, like `$"Name: {name}"`.

- **By Value:** Copies the value; changes don’t affect the original.
- **By Reference:** Passes the address; changes affect the original.

```csharp
void ByValue(int x) { x = 10; }
void ByRef(ref int x) { x = 10; }

int n = 5;
ByValue(n);     // n stays 5
ByRef(ref n);   // n becomes 10
```

---

### **2.5 What do you mean by value type and reference type? Give an example for each.**
- **Value Type:** Holds data directly. Example: `int a = 10;`
- **Reference Type:** Holds a reference to data. Example: `string s = "Hi";`

---

### **2.6 Why namespace is used in C#? How to create and use the namespace in C#? Explain with example.**
Namespaces organize code and prevent name clashes.

```csharp
namespace MySpace {
    class Test {
        public static void SayHi() { Console.WriteLine("Hi"); }
    }
}

class Program {
    static void Main() {
        MySpace.Test.SayHi();  // Using namespace
    }
}
```

---

### **2.7 What is variable size array? Write a C# program to create multidimensional array to store the marks of three student in different subjects...**
A variable size array (jagged array) has rows of different lengths.

```csharp
int[][] marks = new int[3][];
marks[0] = new int[] { 80, 85, 90 };     // 3 subjects
marks[1] = new int[] { 70, 75, 80, 85 }; // 4 subjects
marks[2] = new int[] { 60, 65 };         // 2 subjects

for (int i = 0; i < marks.Length; i++) {
    Console.Write($"Student {i + 1}: ");
    int sum = 0;
    for (int j = 0; j < marks[i].Length; j++) {
        Console.Write(marks[i][j] + " ");
        sum += marks[i][j];
    }
    Console.WriteLine($" Avg: {sum / marks[i].Length}");
}
```

---

### **2.8 What is named argument? Explain with suitable program, how to create alias for namespace in C#?**
Named arguments let you specify parameter names when calling a method.

```csharp
void Show(int a, int b) { Console.WriteLine(a + " " + b); }
Show(b: 20, a: 10);  // Named arguments
```

Alias for namespace:
```csharp
using Alias = System;
Alias.Console.WriteLine("Hello");
```

---

### **2.9 Differentiate between struct and enum. Why do we need to handle the exception? Illustrate with an example with your own customized exception.**
- **Struct:** Holds data and methods (value type).  
- **Enum:** A list of named values.

We handle exceptions to stop crashes and show useful messages.

```csharp
class MyError : Exception {
    public MyError(string msg) : base(msg) {}
}

try {
    throw new MyError("Something went wrong!");
} catch (MyError e) {
    Console.WriteLine(e.Message);
}
```

---

## **3. Object-Oriented Programming in C#**

### **3.1 What is interface? Explain with suitable program, how interface can be used to perform multiple inheritance?**
An interface is a set of rules (methods) a class must follow. It allows multiple inheritance by letting a class use more than one interface.

```csharp
interface IA { void MethodA(); }
interface IB { void MethodB(); }

class MyClass : IA, IB {
    public void MethodA() { Console.WriteLine("A"); }
    public void MethodB() { Console.WriteLine("B"); }
}
```

---

### **3.2 What are use of finalizer in C#? Explain with suitable program, how base keyword is used to call member function and constructor of parent class?**
A finalizer (`~ClassName`) cleans up resources before an object is removed.

**Base keyword:**
```csharp
class Parent {
    public Parent() { Console.WriteLine("Parent"); }
    public void Show() { Console.WriteLine("Parent Show"); }
}

class Child : Parent {
    public Child() : base() { Console.WriteLine("Child"); }
    public void CallBase() { base.Show(); }
}
```

---

### **3.3 What are sealed classes in C#? Write a C# program to illustrate the concept of abstract class and abstract method.**
Sealed classes can’t be inherited (`sealed` keyword).

```csharp
abstract class Shape {
    public abstract void Draw();  // Must be overridden
}

class Circle : Shape {
    public override void Draw() { Console.WriteLine("Circle"); }
}
```

---

### **3.4 What is virtual method? Write a program to illustrate multi-level inheritance with virtual method.**
A virtual method can be changed in a child class using `override`.

```csharp
class Animal {
    public virtual void Sound() { Console.WriteLine("Generic"); }
}
class Dog : Animal {
    public override void Sound() { Console.WriteLine("Woof"); }
}
class Puppy : Dog {
    public override void Sound() { Console.WriteLine("Yip"); }
}
```

---

### **3.5 What is an interface? How interface is used in multiple inheritance? Explain with example.**
See 3.1 for explanation and example.

---

### **3.6 What do you mean by static class and constructor? Explain with suitable example.**
- **Static Class:** Can’t create objects, only has static members.  
- **Static Constructor:** Runs once to set up static stuff.

```csharp
static class Tool {
    static Tool() { Console.WriteLine("Setup"); }
    public static void Use() { Console.WriteLine("Working"); }
}
```

---

### **3.7 Differentiate Object Oriented Programming and Object Based Programming. Explain some of the major features of C# language.**
- **OOP:** Has inheritance, polymorphism, etc. (e.g., C#).  
- **Object-Based:** Uses objects but no inheritance (e.g., JavaScript).

C# Features: OOP, type safety, garbage collection, LINQ.

---

### **3.8 What do you mean by property in C# language? How it is different from method? Compare automatic property with other types of property with suitable example.**
A property controls access to a field. A method does actions.

- **Auto Property:** Simple, no logic (`public int Age { get; set; }`).  
- **Manual Property:** Has logic.

```csharp
class Person {
    public int Age { get; set; }  // Auto
    private int score;
    public int Score { get { return score; } set { score = value; } }  // Manual
}
```

---

### **3.9 Define constructor. Explain different types of constructors used in C# with example.**
A constructor sets up an object when it’s created.

Types:
```csharp
class Car {
    public Car() { }               // Default
    public Car(string n) { }       // Parameterized
    public Car(Car c) { }          // Copy
    static Car() { }               // Static
}
```

---

### **3.10 Explain concept of static class and static constructor with suitable program.**
See 3.6 for explanation and example.

---

### **3.11 Write short notes on: Copy constructor.**
A copy constructor makes a new object by copying another object’s data.

```csharp
class Person {
    public string Name;
    public Person(Person p) { Name = p.Name; }
}
```

---

### **3.12 How virtual method is used to achieve dynamic binding in C#? Explain with the help of suitable program.**
Dynamic binding means the method to call is decided at runtime. Virtual methods make this happen.

```csharp
class Animal {
    public virtual void Sound() { Console.WriteLine("Noise"); }
}
class Cat : Animal {
    public override void Sound() { Console.WriteLine("Meow"); }
}
Animal a = new Cat();
a.Sound();  // Prints "Meow"
```

---

### **3.13 Define dynamic binding in C#? Explain with the help of suitable program.**
Dynamic binding chooses the method at runtime. See 3.12 for example.

---

## **4. Advanced C# Features**

### **4.1 What is an event? Explain with suitable program, how event is handled in C#.**
An event lets objects send messages to each other.

```csharp
class Button {
    public event Action OnClick;
    public void Click() { OnClick?.Invoke(); }
}

class Program {
    static void Main() {
        Button b = new Button();
        b.OnClick += () => Console.WriteLine("Clicked!");
        b.Click();
    }
}
```

---

### **4.2 What is Lambda expression? Explain the concept of generic delegates with suitable program.**
A lambda expression is a short, nameless function (e.g., `x => x * 2`).

**Generic Delegate:**
```csharp
Func<int, int> square = x => x * x;
Console.WriteLine(square(5));  // Prints 25
```

---

### **4.3 How this keyword is used to declare indexer? Write C# program to overload unary (++) and relational (==) operator.**
`this` makes a class act like an array.

```csharp
class MyList {
    int[] data = new int[3];
    public int this[int i] { get { return data[i]; } set { data[i] = value; } }
}

class Num {
    public int Value;
    public static Num operator ++(Num n) { n.Value++; return n; }
    public static bool operator ==(Num a, Num b) { return a.Value == b.Value; }
    public static bool operator !=(Num a, Num b) { return !(a == b); }
}
```

---

### **4.4 What is different between index and properties? Explain the concept of generic class in C# with suitable program.**
- **Indexer:** Uses `[]` to access data.  
- **Property:** Uses a name to access data.

**Generic Class:**
```csharp
class Box<T> {
    public T Item { get; set; }
}
Box<int> b = new Box<int> { Item = 10 };
```

---

### **4.5 What are different type of delegate in C#? Write a C# Program to create a class "Time"...**
Types: Single-cast (one method), Multicast (many methods).

```csharp
class Time {
    public int H, M, S;
    public Time(int h, int m, int s) { H = h; M = m; S = s; }
    public void DisplayTime() { Console.WriteLine($"{H}:{M}:{S}"); }
    public static Time operator +(Time t1, Time t2) {
        int s = t1.S + t2.S;
        int m = t1.M + t2.M + s / 60;
        int h = (t1.H + t2.H + m / 60) % 24;
        return new Time(h, m % 60, s % 60);
    }
    public static bool operator <(Time t1, Time t2) {
        return t1.H < t2.H || (t1.H == t2.H && t1.M < t2.M);
    }
    public static bool operator >(Time t1, Time t2) { return t2 < t1; }
}
```

---

### **4.6 What do you mean by Operator Overloading? Write a C# program to demonstrate binary and relational operator overloading.**
Operator overloading lets you define how operators work with your class.

```csharp
class Point {
    public int X;
    public static Point operator +(Point a, Point b) { return new Point { X = a.X + b.X }; }
    public static bool operator <(Point a, Point b) { return a.X < b.X; }
    public static bool operator >(Point a, Point b) { return b < a; }
}
```

---

### **4.7 What is generics? List different types of generic classes. Explain delegate with example.**
Generics let you use any data type with a class or method.

Types: `List<T>`, `Dictionary<TKey, TValue>`.

```csharp
delegate int Calc(int x);
Calc add = x => x + 1;
Console.WriteLine(add(5));  // Prints 6
```

---

### **4.8 What do you mean by lambda expression? Explain different types of lambda expression used in C# with example.**
See 4.2 for definition. Types:
- **Expression:** `x => x + 1`
- **Statement:** `x => { Console.WriteLine(x); return x; }`

```csharp
Action<int> print = x => Console.WriteLine(x);
print(10);
```

---

### **4.9 What is static binding? Write a C# program to add and subtract two complex number using binary operator overloading.**
Static binding decides the method at compile time.

```csharp
class Complex {
    public int Real;
    public static Complex operator +(Complex a, Complex b) { return new Complex { Real = a.Real + b.Real }; }
    public static Complex operator -(Complex a, Complex b) { return new Complex { Real = a.Real - b.Real }; }
}
```

---

### **4.10 Why Delegate is used in C#? Write a C# program to select odd and divisible by 3 number from list of number (1-30) using LINQ query.**
Delegates let you pass methods like variables.

```csharp
var numbers = Enumerable.Range(1, 30);
var result = numbers.Where(n => n % 2 != 0 && n % 3 == 0);
foreach (int n in result) Console.WriteLine(n);
```

---

### **4.11 Write short notes on: Indexer.**
An indexer lets you use `[]` on a class. See 4.3 for example.

---

### **4.12 Write short notes on: Lambda Expression.**
See 4.2 for explanation.

---

### **4.13 Define operator overloading. Write a C# program to overload unary operator.**
See 4.6 for definition.

```csharp
class Count {
    public int Value;
    public static Count operator ++(Count c) { c.Value++; return c; }
}
```

---

## **5. Exception Handling**

### **5.1 What are keyword used in exception handling? Write a C# program to handle IndexOutOfRangeException and InvalidCastException.**
Keywords: `try`, `catch`, `finally`, `throw`.

```csharp
try {
    int[] arr = new int[2];
    arr[5] = 10;           // IndexOutOfRange
    object o = "text";
    int x = (int)o;        // InvalidCast
} catch (IndexOutOfRangeException) {
    Console.WriteLine("Out of range");
} catch (InvalidCastException) {
    Console.WriteLine("Bad cast");
}
```

---

### **5.2 What is an Exception? Write a program to generate divide by zero exception and index out of Range exception and also handle these exception.**
An exception is an error that stops the program.

```csharp
try {
    int x = 10 / 0;       // DivideByZero
    int[] arr = { 1 };
    arr[2] = 5;           // IndexOutOfRange
} catch (DivideByZeroException) {
    Console.WriteLine("Can’t divide by zero");
} catch (IndexOutOfRangeException) {
    Console.WriteLine("Out of range");
}
```

---

### **5.3 What is SystemException? Write a C# program that will read balance and withdraw amount...**
`SystemException` is the base for built-in exceptions.

```csharp
Console.Write("Balance: ");
double bal = double.Parse(Console.ReadLine());
Console.Write("Withdraw: ");
double w = double.Parse(Console.ReadLine());
if (bal >= w) {
    Console.WriteLine($"Remaining: {bal - w}");
} else {
    throw new ApplicationException("Not enough money");
}
```

---

### **5.4 Write a program for handling exception in ASP.NET.**
In ASP.NET, use `try-catch` or `web.config`.

```aspx
try {
    int x = 10 / 0;
} catch (Exception ex) {
    Response.Write("Error: " + ex.Message);
}
```

---

## **6. LINQ**

### **6.1 What is query syntax in LINQ? Explain the standard query operators "select", "contains", "orderBy" and "where"...**
Query syntax is like SQL for LINQ.

- **select:** Picks data.
- **contains:** Checks if something’s in a list.
- **orderBy:** Sorts data.
- **where:** Filters data.

```csharp
int[] nums = { 1, 2, 3 };
var q = from n in nums where n > 1 orderby n select n;
```

---

### **6.2 What is a Query expression? Write a C# program to select Students who are lived in Kirtipur and studied in Patan Multiple Campus using LINQ.**
A query expression is a LINQ query.

```csharp
class Student { public string Address, Campus; }
var students = new List<Student> { new Student { Address = "Kirtipur", Campus = "Patan Multiple Campus" } };
var result = from s in students
             where s.Address == "Kirtipur" && s.Campus == "Patan Multiple Campus"
             select s;
```

---

### **6.3 List any five LINQ standard operators? Write a program to compute aggregate salary...**
Operators: `Where`, `Select`, `OrderBy`, `Sum`, `Count`.

```csharp
class Emp { public double Salary; }
var emps = new List<Emp> { new Emp { Salary = 1000 }, new Emp { Salary = 2000 } };
double total = emps.Sum(e => e.Salary);
var sorted = emps.OrderByDescending(e => e.Salary);
```

---

### **6.4 What is LINQ? Write a program to select employees whose salary is greater than 20000 and whose address is kathmandu using LINQ.**
LINQ lets you query data easily.

```csharp
class Emp { public double Salary; public string Address; }
var emps = new List<Emp> { new Emp { Salary = 25000, Address = "Kathmandu" } };
var result = emps.Where(e => e.Salary > 20000 && e.Address == "Kathmandu");
```

---

### **6.5 What is LINQ? Write a program...**
See 6.4.

---

## **7. ASP.NET**

### **7.1 What are component of ASP.NET? Explain various validation server control in ASP.NET with suitable program.**
Components: Web Forms, MVC, Web API.

Validation controls:
- **RequiredFieldValidator:** Checks if a field is filled.
- **RangeValidator:** Checks a range.

```aspx
<asp:TextBox ID="txt" runat="server" />
<asp:RequiredFieldValidator ControlToValidate="txt" ErrorMessage="Required" runat="server" />
```

---

### **7.2 Write a program to create form for calculating simple interest...**
**Page1.aspx:**
```aspx
<asp:TextBox ID="txtP" runat="server" /> <!-- Principal -->
<asp:TextBox ID="txtR" runat="server" /> <!-- Rate -->
<asp:TextBox ID="txtT" runat="server" /> <!-- Time -->
<asp:Button ID="btn" runat="server" OnClick="btn_Click" Text="Calculate" />
```
**Code:**
```csharp
protected void btn_Click(object sender, EventArgs e) {
    double si = double.Parse(txtP.Text) * double.Parse(txtR.Text) * double.Parse(txtT.Text) / 100;
    Session["SI"] = si;
    Response.Redirect("Page2.aspx");
}
```
**Page2.aspx:**
```aspx
<asp:Label ID="lbl" runat="server" />
```
```csharp
lbl.Text = Session["SI"].ToString();
```

---

### **7.3 What is web server control in ASP.NET? List five web server control...**
Web server controls are server-side UI elements.  
Controls: `TextBox`, `Button`, `Label`, `CheckBox`, `DropDownList`.

See 7.2 for a similar example.

---

### **7.4 Write a program to create user registration form...**
See 7.2, just change fields to user data (e.g., Name, Email).

---

### **7.5 Write a program for handling exception in ASP.NET.**
See 5.4.

---

### **7.6 Suppose you are hired by a reputed software company...**
**Employee.aspx:**
```aspx
<asp:TextBox ID="txtEmpNo" runat="server" /> <!-- Add all fields -->
<asp:Button ID="btnSave" runat="server" OnClick="btnSave_Click" Text="Save" />
```
**Code:**
```csharp
protected void btnSave_Click(object sender, EventArgs e) {
    using (SqlConnection conn = new SqlConnection("connection_string")) {
        conn.Open();
        string sql = "INSERT INTO Employee (EmpNo, Name) VALUES (@EmpNo, @Name)"; // Add all fields
        SqlCommand cmd = new SqlCommand(sql, conn);
        cmd.Parameters.AddWithValue("@EmpNo", txtEmpNo.Text);
        // Add other parameters
        cmd.ExecuteNonQuery();
    }
}
```

---

## **8. Database Connectivity with ADO.NET**

### **8.1 What is difference between executeScalar() and executeReader() method? Write a C# program...**
- **ExecuteScalar:** Gets one value (e.g., a count).
- **ExecuteReader:** Gets rows of data.

```csharp
using (SqlConnection conn = new SqlConnection("connection_string")) {
    conn.Open();
    SqlCommand cmd = new SqlCommand("INSERT INTO Customer (Account_no, Name, Balance) VALUES (1, 'A', 6000)", conn);
    cmd.ExecuteNonQuery(); // Repeat for 5
    cmd.CommandText = "SELECT * FROM Customer WHERE Balance > 5000";
    SqlDataReader r = cmd.ExecuteReader();
    while (r.Read()) Console.WriteLine(r["Name"]);
}
```

---

### **8.2 Explain difference between ExecuteReader and ExecuteNonQuery...**
- **ExecuteReader:** Reads data.
- **ExecuteNonQuery:** Changes data (INSERT, UPDATE).

```csharp
using (MySqlConnection conn = new MySqlConnection("connection_string")) {
    conn.Open();
    MySqlCommand cmd = new MySqlCommand("SELECT * FROM Product WHERE UnitPrice > 1000", conn);
    MySqlDataReader r = cmd.ExecuteReader();
    while (r.Read()) Console.WriteLine(r["ProductName"]);
    r.Close();
    cmd.CommandText = "UPDATE Product SET UnitPrice = 4500 WHERE ProductId = 50";
    cmd.ExecuteNonQuery();
}
```

---

### **8.3 Write a C# program to show insert and select operation in database.**
See 8.1.

---

### **8.4 Write a C# program to show insert and select operation in database.**
See 8.1.

---

### **8.5 What are differences between Data Adapter and Data Reader in ADO.NET?**
- **DataReader:** Reads data fast, one-way.
- **DataAdapter:** Fills a table for offline use.

--- 
