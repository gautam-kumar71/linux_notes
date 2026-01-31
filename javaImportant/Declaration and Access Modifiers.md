
---

## **Java Source File Structure**

###  General Rules:

- A Java program can contain **any number of classes**.
    
- **At most one class** can be declared as `public`.
    
- If there is a **public class**, then:  
    👉 **File name = Public class name**, otherwise **compile-time error**.
    
- If there is **no public class**, then:  
    👉 We can give **any name** to the source file.
    

---

## **Case 1: No Public Class**

- If there is **no public class**, then:  
    👉 We can use **any name** for the Java file.
    
- There are **no restrictions**.
    

### Example:

```java
A.java  
B.java  
C.java  
Ashok.java
```

---

## **Case 2: One Public Class**

- If class `B` is declared as `public`:  
    👉 File name must be **B.java**.
    
- Otherwise, we get **compile-time error**:
    

```java
class B is public, should be declared in a file named B.java
```

---

## **Case 3: More Than One Public Class**

- If both `B` and `C` are declared as `public` and file name is `B.java`:  
    👉 We get **compile-time error**:
    

```java
class C is public, should be declared in a file named C.java
```

- **Recommendation:**  
    👉 Use **only one class per file**.  
    👉 File name should be **same as class name**.  
    👉 This improves **readability and understanding**.
    

---

## **Example Program**

```java
class A  
{  
    public static void main(String args[]){  
        System.out.println("A class main method is executed");  
    }  
}  

class B  
{  
    public static void main(String args[]){  
        System.out.println("B class main method is executed");  
    }  
}  

class C  
{  
    public static void main(String args[]){  
        System.out.println("C class main method is executed");  
    }  
}  

class D  
{  
}  
```

---

![[Pasted image 20260131142523.png]]

## **Program Execution**

```java
D:\Java>java A  
A class main method is executed  

D:\Java>java B  
B class main method is executed  

D:\Java>java C  
C class main method is executed  

D:\Java>java D  
Exception in thread "main" java.lang.NoSuchMethodError: main  

D:\Java>java Ashok  
Exception in thread "main" java.lang.NoClassDefFoundError: Ashok  
```

---

## **Important Points**

###  Compilation:

- We can **compile a Java program**, not individual classes.
    
- For **each class**, one `.class` file is created.
    

###  Execution:

- We can **run a class**, not a `.java` file.
    
- When we run a class:  
    👉 Its `main()` method is executed.
    

###  Main Method Error:

- If a class **does not contain `main()` method**:  
    👉 Runtime error:
    

```java
NoSuchMethodError: main
```

###  Class File Not Found Error:

- If `.class` file is **not available**:  
    👉 Runtime error:
    

```java
NoClassDefFoundError: Ashok
```

---
#vvi 

`When using java File.java (Java 11+), if no class matches the file name, Java executes the first class that contains a main() method.If there is no main method in the first class then it will give error during runtime`

`Error: Could not find or load main class Test`

---
---
---

## **Import Statement**

### Example (Without Import)

```java
class Test{  
    public static void main(String args[]){  
        ArrayList l = new ArrayList();  
    }  
}  
```

### Output:

```
Compile time error.

D:\Java>javac Test.java  
Test.java:3: cannot find symbol  
symbol  : class ArrayList  
location: class Test  

ArrayList l = new ArrayList();
```

### Reason:

- `ArrayList` belongs to `java.util` package.
    
- Without import, compiler **cannot find** the class.
    

---

## **Using Fully Qualified Name**

We can write:

```java
java.util.ArrayList l = new java.util.ArrayList();
```

### Problem:

- Code becomes **long**.
    
- **Readability decreases**.
    

---

## **Using Import Statement (Recommended Way)**

### Example:

```java
import java.util.ArrayList;  

class Test{  
    public static void main(String args[]){  
        ArrayList l = new ArrayList();  
    }   
}
```

### Output:

```
D:\Java>javac Test.java
```

### Advantage:

- No need to use full name.
    
- We can use **short class name**.
    
- Code becomes **short and readable**.
    

---

## **Conclusion**

- When we use **import**, no need for full class name.
    
- When we use **full class name**, no need for import.
    
- Import reduces **code length** and improves **readability**.
    

---

## **Case 1: Types of Import Statements**

There are **2 types** of import statements:

1. Explicit Class Import
    
2. Implicit Class Import
    

---

## **Explicit Class Import**

### Example:

```java
import java.util.ArrayList;
```

### Points:

- Imports **only one class**.
    
- Highly recommended.
    
- Improves readability.
    
- Best for **professional / hi-tech environment**.


---

## **Implicit Class Import**

### Example:

```java
import java.util.*;
```

### Points:

- Imports **all classes** from the package.
    
- It is **not recommended**.
    
- Reduces **readability** (we don’t know which class is used).
    
- Best suitable where **fast typing is important** (like training centers).
    

---

## **Case 2: Meaningful Import Statements**

### Question:

Which of the following import statements are meaningful?

![[Pasted image 20260131151623.png]]
---

## **Case 3: Using Fully Qualified Name**

### Example:

```java
class MyArrayList extends java.util.ArrayList  
{  
}  
```

### Points:

- Program compiles **without import**.
    
- Because full name is used.
    
- If we use full name → no import needed.
    
- If we use import → no full name needed.
    

---

## **Case 4: Ambiguity Problem**

### Example:

```java
import java.util.*;  
import java.sql.*;  

class Test  
{  
    public static void main(String args[])  
    {  
        Date d = new Date();  
    }
}
```

### Output:

```
Compile time error.

reference to Date is ambiguous,  
both class java.sql.Date in java.sql  
and class java.util.Date in java.util match
```

### Reason:

- `Date` class exists in **both packages**.
    
- Compiler gets **confused**.
    

### Note:

- Same problem can happen with `List` (in `util` and `awt`).
    

---

## **Case 5: Priority While Resolving Class Names**

Compiler checks class names in this order:

1️⃣ Explicit Class Import  
2️⃣ Current Working Directory  
3️⃣ Implicit Class Import (`*`)

---

### Example:

```java
import java.util.Date;  
import java.sql.*;  

class Test  
{  
    public static void main(String args[]){  
        Date d = new Date();  
    }
}
```

### Result:

- Program compiles successfully.
    
- `java.util.Date` is used.
    
- Because explicit import has **highest priority**.
    

---

## **Case 6: Importing Packages**

### Rule:

- When we import a package:  
    👉 All **classes and interfaces** in that package are available.  
    👉 **Sub-package classes are NOT available**.
    

### Example:

```java
import java.util.*;
```

- Imports all classes in `java.util`.
- Does NOT import `java.util.concurrent` (sub-package).

![[Pasted image 20260131150621.png]]

---
## **Case 7: Default Imported Packages**

### Rule:

In every Java program, these **2 packages are available by default**, so we do NOT need to import them:

1️⃣ `java.lang` package  
2️⃣ Default package (current working directory)

### Examples of `java.lang`:

- `String`
    
- `System`
    
- `Math`
    
- `Object`
    

👉 These classes can be used **without import**.

---

## **Case 8: Import Statement – Compile Time Concept**

### Rule:

- Import statements work **only at compile time**.
    
- More imports → **More compile time**.
    
- Imports do **NOT affect execution time**.
    

👉 Runtime speed remains the same.

---

## **Class Loading and Import Statement**

### Important Point:

- When we write an import statement:  
    👉 `.class` file is **NOT loaded immediately**.
    
- The `.class` file is loaded:  
    👉 Only when the class is **actually used** in the program.
    

### Example:

If we import `ArrayList` but never use it:

- `ArrayList.class` will NOT be loaded.
    

---

## **Dynamic Loading (Load-on-Demand)**

This behavior is called:

✔️ **Dynamic Loading**  
✔️ **Load-on-Demand**  
✔️ **Load-on-Fly**

### Meaning:

- Classes are loaded **only when needed**.
    
- Not at import time.
    
- Improves performance and memory usage.
    

---
#todo 
Static and normal imports,package

---
#note :An empty source file is also a valid java program

---
---
---
## **Modifiers for Top-Level Classes**

### Rule:

Only the following **5 modifiers** are allowed for **top-level classes** (outer classes):

1️⃣ `public`  
2️⃣ `default` (no modifier)  
3️⃣ `final`  
4️⃣ `abstract`  
5️⃣ `strictfp`

👉 If we use **any other modifier**, we get **compile-time error**.

---

## **Invalid Modifier Example**

### Example:

```java
private class Test 
{ 
    public static void main(String args[]){ 
        int i = 0; 
        for(int j = 0; j < 3; j++) 
        { 
            i = i + j; 
        } 
        System.out.println(i); 
    }
}
```

### Output:

```
Compile time error.

D:\Java>javac Test.java 
Test.java:1: modifier private not allowed here
private class Test
```

### Reason:

- `private` is **not allowed** for top-level classes.
    

---

## **Modifiers for Inner Classes**

### Rule:

- For **inner classes**, more modifiers are allowed.
    
- They can use:  
    👉 `private`, `protected`, `static`, etc.
    

👉 (These are **not allowed** for top-level classes.)

![[Pasted image 20260131155745.png]]

---
---
---
## **Public Classes**

### Rule:

- If a class is declared as `public`:  
    👉 It can be accessed **from anywhere**  
    👉 Inside the package and **outside the package**
    

---

### Example:

#### **Program 1**

```java
package pack1; 

public class Test 
{ 
    public void methodOne(){ 
        System.out.println("test class methodone is executed"); 
    }
}
```

#### Compile:

```
D:\Java>javac -d . Test.java
```

---

#### **Program 2**

```java
package pack2; 

import pack1.Test; 

class Test1 
{ 
    public static void main(String args[]){ 
        Test t = new Test(); 
        t.methodOne(); 
    }
}
```

#### Output:

```
D:\Java>javac -d . Test1.java  
D:\Java>java pack2.Test1  

test class methodone is executed
```

---

### If `Test` is NOT public:

- Compile-time error:
    

```
pack1.Test is not public in pack1; cannot be accessed from outside package
```

---

## **Default Classes (Package Level Access)**

### Rule:

- If a class has **no access modifier**:  
    👉 It can be accessed **only within the same package**
    
- Hence called **package-level access**.
    

---

### Example:

#### **Program 1**

```java
package pack1; 

class Test 
{ 
    public void methodOne(){ 
        System.out.println("test class methodone is executed"); 
    }
}
```

#### **Program 2**

```java
package pack1; 

class Test1 
{ 
    public static void main(String args[]){ 
        Test t = new Test(); 
        t.methodOne(); 
    }
}
```

#### Output:

```
D:\Java>javac -d . Test.java  
D:\Java>javac -d . Test1.java  
D:\Java>java pack1.Test1  

test class methodone is executed
```

---

## **Final Modifier**

### Rule:

- `final` can be used with:  
    👉 Classes  
    👉 Methods  
    👉 Variables
    

---

## **Final Methods**

### Rule:

- Methods of parent are available to child by default.
    
- If child **must not override** a method:  
    👉 Declare that method as `final`.
    
- **Final methods cannot be overridden**.
    

---

### Example:

#### **Program 1**

```java
class Parent 
{ 
    public void property(){ 
        System.out.println("cash+gold+land"); 
    } 

    public final void marriage(){ 
        System.out.println("subbalakshmi"); 
    }
}
```

#### **Program 2**

```java
class child extends Parent 
{ 
    public void marriage(){ 
        System.out.println("Thamanna"); 
    }
}
```

#### Output:

```
Compile time error.

marriage() in child cannot override marriage() in Parent;  
overridden method is final
```

---

## **Final Class**

### Rule:

- If a class is declared `final`:  
    👉 We **cannot create child classes**  
    👉 Inheritance is NOT allowed.
    

---

### Example:

#### **Program 1**

```java
final class Parent 
{ 
}
```

#### **Program 2**

```java
class child extends Parent 
{ 
}
```

#### Output:

```
Compile time error.

cannot inherit from final Parent
```

---

### Note:

- All methods inside a `final` class are **final by default**.
    
- Variables inside a `final` class:  
    👉 **Need not be final**.
    

---

### Example:

```java
final class Parent 
{ 
    static int x = 10; 

    static { 
        x = 999; 
    }
}
```

---

## **Final Keyword – Pros & Cons**

### Advantage:

✔️ Improves **security**

### Disadvantages:

❌ No **polymorphism** (final methods)  
❌ No **inheritance** (final classes)

### Recommendation:

👉 If there is **no strong requirement**,  
👉 **Do NOT use `final` keyword**.

---

## **Abstract Modifier**

### Rule:

- `abstract` is applicable to:  
    👉 Classes  
    👉 Methods
    
- NOT applicable to variables.
    

---

## **Abstract Methods**

### Rule:

- Abstract methods:  
    👉 Have **only declaration**  
    👉 Have **no implementation**
    
- Must end with **semicolon (`;`)**.
    

---

### Example:

```java
abstract class Test 
{ 
    public abstract void methodOne(); 
}
```

![[Pasted image 20260131161802.png]]

---
`Child classes are responsible to provide implementation for parent class abstract methods.`

![[Pasted image 20260131161951.png]]


---

## **Advantage of Abstract Methods**

- Main advantage:  
    👉 By declaring abstract methods in the parent class, we give **guidelines** to child classes.  
    👉 Child classes must **compulsorily implement** those methods.
    

---

## **Abstract and Implementation Modifiers**

- Abstract methods:  
    👉 Do NOT talk about implementation.
    
- If any modifier talks about implementation:  
    👉 That modifier becomes **enemy** to `abstract`.  
    👉 Such combination is **illegal**.
---
![[Pasted image 20260131162248.png]]

Here are your **short and simple notes**, using **only the information you provided**, without adding anything extra:

---

## **Abstract Class**

- If we are **not allowed to create an object** of a class:  
    👉 Declare it as `abstract`.
    
- For abstract class, **instantiation is not possible**.
    

---

### Example:

```java
abstract class Test 
{ 
    public static void main(String args[]){ 
        Test t = new Test(); 
    }
}
```

### Output:

```
Compile time error.

Test is abstract; cannot be instantiated
```

---

## **Difference Between Abstract Class and Abstract Method**

### 1. Abstract Method in a Class

- If a class contains **at least one abstract method**:  
    👉 The class must be declared as `abstract`.
    
- Because implementation is incomplete.
    
- We cannot create object of that class.
    

---

### 2. Abstract Class Without Abstract Methods

- Even if a class has **no abstract methods**:  
    👉 We can still declare it as `abstract`.
    
- An abstract class can contain **zero abstract methods**.
    

---

### Examples:

- `HttpServlet` class is abstract but has no abstract methods.
    
- Adapter classes are abstract but have no abstract methods.
    

---

## **Invalid Abstract Method Examples**

### Example 1:

```java
class Parent 
{ 
    public void methodOne(); 
}
```

### Output:

```
Compile time error.
missing method body, or declare abstract
```

---

### Example 2:

```java
class Parent 
{ 
    public abstract void methodOne(){} 
}
```

### Output:

```
Compile time error.
abstract methods cannot have a body
```

---

### Example 3:

```java
class Parent 
{ 
    public abstract void methodOne(); 
}
```

### Output:

```
Compile time error.
Parent is not abstract and does not override abstract method
```

---

## **Abstract Class and Inheritance**

- If a class extends an abstract class:  
    👉 It must implement **all abstract methods**.
    
- Otherwise:  
    👉 The child class must be declared as `abstract`.
    

---

### Example:

```java
abstract class Parent 
{ 
    public abstract void methodOne(); 
    public abstract void methodTwo(); 
} 

class child extends Parent 
{ 
    public void methodOne(){} 
}
```

### Output:

```
Compile time error.

child is not abstract and does not override methodTwo()
```

---

### Note:

- If `child` is declared as abstract:  
    👉 Code compiles fine.  
    👉 Child of child must implement `methodTwo()`.
    

---

## **Difference Between Final and Abstract**

### Methods:

- Abstract method:  
    👉 Must be overridden.
    
- Final method:  
    👉 Cannot be overridden.
    
- So, `final abstract` is **illegal for methods**.
    

---

### Classes:

- Abstract class:  
    👉 Child class must provide implementation.
    
- Final class:  
    👉 Cannot have child class.
    
- So, `final abstract` is **illegal for classes**.
    

---

![[Pasted image 20260131163041.png]]

An **abstract class** can contain **final methods**.
### Reason

An abstract class is:
> A class meant to be **extended**, but **not fully implemented**.

So it can have:

- Some methods **incomplete** → `abstract`    
- Some methods **complete** → normal / `final`

A `final` class **cannot be abstract** and **cannot have abstract methods**.

### Reason

A `final` class means:
> “I cannot be inherited.”

But abstract methods mean:
> “Child must override me.”