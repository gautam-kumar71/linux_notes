
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


Here are your **short and simple notes**, using **only the information you provided**, without adding anything extra:

---

## **Member Modifiers**

---

## **Public Members**

### Rule:

- If a member is declared as `public`:  
    👉 We can access it from anywhere.
    
- But the **corresponding class must be visible (public)**.
    
- First check **class visibility**, then member visibility.
    

---

### Example:

#### **Program 1**

```java
package pack1; 

class A 
{ 
    public void methodOne(){ 
        System.out.println("a class method"); 
    }
}
```

#### Compile:

```
D:\Java>javac -d . A.java
```

---

#### **Program 2**

```java
package pack2; 

import pack1.A; 

class B 
{ 
    public static void main(String args[]){ 
        A a = new A(); 
        a.methodOne(); 
    }
}
```

---

### Output:

```
Compile time error.

pack1.A is not public in pack1;  
cannot be accessed from outside package
```

---

### Conclusion:

- Even though `methodOne()` is public,
    
- We cannot access it because class `A` is not public.
    
- Both **class and member must be public**.
    

---

## **Default Members (Package Level Access)**

### Rule:

- If a member has **no modifier**:  
    👉 It is default.  
    👉 It can be accessed only within the **same package**.
    
- Hence called **package-level access**.
    

---

## **Example 1 (Same Package)**

### Program 1

```java
package pack1; 

class A 
{ 
    void methodOne(){ 
        System.out.println("methodOne is executed"); 
    }
}
```

### Program 2

```java
package pack1; 

class B 
{ 
    public static void main(String args[]){ 
        A a = new A(); 
        a.methodOne(); 
    }
}
```

### Output:

```
methodOne is executed
```

---

## **Example 2 (Different Package)**

### Program 1

```java
package pack1; 

class A 
{ 
    void methodOne(){ 
        System.out.println("methodOne is executed"); 
    }
}
```

### Program 2

```java
package pack2; 

import pack1.A; 

class B 
{ 
    public static void main(String args[]){ 
        A a = new A(); 
        a.methodOne(); 
    }
}
```

---

### Output:

```
Compile time error.

pack1.A is not public in pack1;  
cannot be accessed from outside package
```

---

## ✅ Java 11 Special Feature (Optional)

In Java 11, you can run **single-file programs** like this:

`java B.java`

👉 Only works when:

- No package
    
- Single file
    
- Simple program
    

❌ Not recommended when using packages.

---

## **Private Members**

### Rule:

- If a member is declared as `private`:  
    👉 It can be accessed **only within the same class**.
    

---

### Point:

- Private methods are **not visible in child classes** but can be *inherited* and cannot be **accessed**.
    
- Abstract methods must be visible to child classes.
    
- So, `private` + `abstract` is an **illegal combination** for methods.
    

---

## **Protected Members**

### Rule:

- If a member is declared as `protected`:  
    👉 It can be accessed:
    
    - Within the **same package (anywhere)**
        
    - Outside package **only in child classes** using *child reference * and not parent's reference
        

### Formula:

```
Protected = Default + Kids (Child classes)
```

---

### Access in Same Package:

- We can access protected members:  
    👉 By parent reference  
    👉 By child reference
    

---

### Access in Different Package:

- We can access protected members:  
    👉 Only in child classes  
    👉 Only by **child reference**
    
- We cannot use **parent reference** outside package.
    

---

## **Example**

### Program 1

```java
package pack1; 

public class A 
{ 
    protected void methodOne(){ 
        System.out.println("methodOne is executed"); 
    }
}
```

---

### Program 2

```java
package pack1; 

class B extends A 
{ 
    public static void main(String args[]){ 

        A a = new A(); 
        a.methodOne(); 

        B b = new B(); 
        b.methodOne(); 

        A a1 = new B(); 
        a1.methodOne(); 
    }
}
```

---

### Output:

```
methodOne is executed  
methodOne is executed  
methodOne is executed
```

---

## **Protected Access (From Image Example)**

- From outside package:  
    ❌ Using parent reference → Not allowed  
    ✔️ Using child reference → Allowed
    
- So:
    
    ```
    A a = new A();   ❌
    C c = new C();   ✔️
    A a1 = new B();  ❌
    ```
    

![[Pasted image 20260131201410.png]]

#vvi
 Here, import pack1.B; is missing without that it will say that cannot find symbol B.
 And here, import pack1.B cannot be used because

 `A default (package-private) class cannot be imported into another package because it is accessible only within its own package.`
 
---
![[Pasted image 20260131204227.png]]                    

`Private<default<protected<public`
`Recommended modifier for variables is private where as recommended modifier for `
`methods is public`

---

### **Final Variables – Final Instance Variables

#### 1. Instance Variables

- If the value of a variable changes from object to object, it is called an **instance variable**.
    
- For every object, a **separate copy** of instance variables is created.
    
- JVM provides **default values** for instance variables if they are not initialized.
    

**Example:**

```java
class Test {
    int i;

    public static void main(String args[]) {
        Test t = new Test();
        System.out.println(t.i);
    }
}
```

**Correct Output:**

```
0
```

---

#### 2. Final Instance Variables

- If an instance variable is declared as `final`, it **must be initialized explicitly**.
    
- JVM **will not provide default values** for final instance variables.
    
- If not initialized, it gives a **compile-time error**, whether we use it or not.
    

---

#### 3. Without `final` (No Error)

**Program:**

```java
class Test {
    int i;
}
```

**Correct Output:**

```
Compiled successfully (No error)
```

---

#### 4. With `final` (Without Initialization – Error)

**Program:**

```java
class Test {
    final int i;
}
```

**Correct Output:**

```
Compile-time error:
variable i might not have been initialized
```

---

#### 5. Rule for Final Instance Variables

- Final instance variables must be initialized **before constructor completion**.
    
- They can be initialized only in the following places:
    

---

### 6. Places Where Initialization is Allowed

---

#### (1) At the Time of Declaration

**Example:**

```java
class Test {
    final int i = 10;
}
```

**Correct Output:**

```
Compiled successfully (No error)
```

---

#### (2) Inside Instance Block

**Example:**

```java
class Test {
    final int i;

    {
        i = 10;
    }
}
```

**Correct Output:**

```
Compiled successfully (No error)
```

---

#### (3) Inside Constructor

**Example:**

```java
class Test {
    final int i;

    Test() {
        i = 10;
    }
}
```

**Correct Output:**

```
Compiled successfully (No error)
```

---

### 7. Initialization in Other Places (Not Allowed)

If we try to initialize a final instance variable anywhere else, we get a compile-time error.

---

#### Example (Inside Method – Error)

```java
class Test {
    final int i;

    public void methodOne() {
        i = 10;
    }
}
```

**Correct Output:**

```
Compile-time error:
cannot assign a value to final variable i
```

---

### 8. Important Points

- Instance variables get default values from JVM.
    
- Final instance variables do **not** get default values.
    
- Final instance variables must be initialized:
    
    - At declaration, or
        
    - In instance block, or
        
    - In constructor.
        
- Initialization inside methods is **not allowed**.
    
- Once initialized, final variables **cannot be changed**.
    

#vvi 
```java
class Test {
    final int i;

    i = 10;   // ❌ Invalid: cannot write statements directly in class body
}
```

---

### **Final Static Variables 

---

### 1. Static Variables

- If the value of a variable does **not change from object to object**, it is **not recommended** to declare it as an instance variable.
    
- Such variables should be declared at **class level** using the `static` keyword.
    
- For instance variables: each object gets a **separate copy**.
    
- For static variables: only **one copy** is created at class level and **shared** by all objects.
    

---

### 2. Default Values for Static Variables

- Static variables get **default values** from JVM.
    
- No need to initialize them explicitly.
    

**Example:**

```java
class Test {
    static int i;

    public static void main(String args[]) {
        System.out.println("value of i is :" + i);
    }
}
```

**Output:**

```
Value of i is: 0
```

---

### 3. Final Static Variables

- If a static variable is declared as `final`, it **must be initialized explicitly**.
    
- JVM **will not provide default values**.
    
- If not initialized, it causes a **compile-time error**, whether used or not.
    

---

### 4. Rule for Final Static Variables

- Final static variables must be initialized **before class loading is completed**.
    
- Otherwise, a compile-time error occurs.
    
- They can be initialized only in the following places:
    

---

### 5. Places Where Initialization is Allowed

---

#### (1) At the Time of Declaration

**Example:**

```java
class Test {
    final static int i = 10;
}
```

**Output:**

```
Compiled successfully (No error)
```

---

#### (2) Inside Static Block

**Example:**

```java
class Test {
    final static int i;

    static {
        i = 10;
    }
}
```

**Output:**

```
Compiled successfully (No error)
```

---

### 6. Initialization in Other Places (Not Allowed)

If we try to initialize a final static variable anywhere else, it gives a compile-time error.

---

#### Example (Inside main Method – Error)

```java
class Test {
    final static int i;

    public static void main(String args[]) {
        i = 10;
    }
}
```

**Output:**

```
Compile-time error:
cannot assign a value to final variable i
```

---

### 7. Important Points

- Static variables are shared by all objects.
    
- Only one copy of static variable exists in memory.
    
- JVM gives default values to normal static variables.
    
- Final static variables do not get default values.
    
- Final static variables must be initialized:
    
    - At declaration, or
        
    - Inside static block.
        
- Initialization inside methods is not allowed.
    
- Once initialized, final static variables cannot be changed.
    



![[Pasted image 20260131223702.png]]

---
### Final Local Variables 

---

### 1. Local Variables

- Variables declared inside a **method, block, or constructor** are called **local variables**.
    
- They are used to meet **temporary requirements** of the programmer.
    
- JVM **does not provide default values** for local variables.
    
- Local variables must be **initialized explicitly before use**.
    

---

### 2. Using Local Variable Without Initialization (No Error if Not Used)

**Example:**

```java
class Test {
    public static void main(String args[]) {
        int i;
        System.out.println("hello");
    }
}
```

**Output:**

```
hello
```

---

### 3. Using Local Variable Without Initialization (Error)

**Example:**

```java
class Test {
    public static void main(String args[]) {
        int i;
        System.out.println(i);
    }
}
```

**Output:**

```
Compile-time error:
variable i might not have been initialized
```

---

### 4. Final Local Variables

- Even if a local variable is declared as `final`, it must be **initialized before use**.
    
- JVM will not provide any default value.
    

---

#### Example:

```java
class Test {
    public static void main(String args[]) {
        final int i;
        System.out.println("hello");
    }
}
```

**Output:**

```
hello
```

---

### 5. Note on Modifiers for Local Variables

- The **only applicable modifier** for local variables is `final`.
    
- If we use any other modifier, it gives a **compile-time error**.
    

---

### 6. Important Points

- Local variables are declared inside methods, blocks, or constructors.
    
- They are used for temporary purposes.
    
- JVM does not give default values to local variables.
    
- Local variables must be initialized before use.
    
- Using an uninitialized local variable causes a compile-time error.
    
- Final local variables also must be initialized before use.
    
- Only `final` is allowed as a modifier for local variables.
    
- Other modifiers are not allowed for local variables.
    

![[Pasted image 20260131224406.png]]

---
### Formal Parameters 

---

### 1. Formal Parameters

- The parameters of a method are called **formal parameters**.
    
- Formal parameters act like **local variables** inside the method.
    
- So, it is possible to declare formal parameters as `final`.
    

---

### 2. Final Formal Parameters

- If formal parameters are declared as `final`, their value **cannot be changed** inside the method.
    

---

### 3. Default Values and Initialization Rules

- For **instance and static variables**:
    
    - JVM provides default values.
        
    - If they are declared as `final`, JVM does not provide default values.
        
    - They must be initialized explicitly, whether used or not.
        
- For **local variables**:
    
    - JVM does not provide default values.
        
    - They must be initialized before use.
        
    - This rule is same for both final and non-final local variables.
        

---

### 4. Important Points

- Formal parameters behave like local variables.
    
- Formal parameters can be declared as `final`.
    
- Final formal parameters cannot be modified inside the method.
    
- JVM gives default values to instance and static variables.
    
- JVM does not give default values to final instance and static variables.
    
- JVM does not give default values to local variables.
    
- Local variables must always be initialized before use.
    
- The initialization rule is same for final and non-final local variables.
    
![[Pasted image 20260131224712.png]]

---
### **Static Modifier (Notes)**

---

### 1. Static Modifier

- `static` is a modifier applicable to:
    
    - Methods
        
    - Variables
        
    - Blocks
        
- We **cannot declare a class as static**.
    
- **Inner classes** can be declared as `static`.
    

---

### 2. Static Variables vs Instance Variables

- For **instance variables**:
    
    - Every object gets a **separate copy**.
        
- For **static variables**:
    
    - Only **one copy** is created at class level.
        
    - It is **shared by all objects** of that class.
        

![[Pasted image 20260131225544.png]]

---
### **Accessing Instance and Static Variables (Notes)**

---

### 1. Access Rules

- Instance variables can be accessed **directly only from instance area**.
    
- Instance variables **cannot be accessed directly from static area**.
    
- Static variables can be accessed **directly from both instance and static areas**.
    

---

### 2. Declarations

1. `int x = 10;` → Instance variable
    
2. `static int x = 10;` → Static variable
    

```java
public void methodOne() {
    System.out.println(x);
}
```

→ Instance method

```java
public static void methodOne() {
    System.out.println(x);
}
```

→ Static method

---

### 3. Which Declarations Are Allowed Together?

---

#### (a) 1 and 3 (Allowed)

**Example:**

```java
class Test {
    int x = 10;

    public void methodOne() {
        System.out.println(x);
    }
}
```

**Output:**

```
Compiled successfully
```

---

#### (b) 1 and 4 (Not Allowed)

**Example:**

```java
class Test {
    int x = 10;

    public static void methodOne() {
        System.out.println(x);
    }
}
```

**Output:**

```
Compile-time error:
non-static variable x cannot be referenced from a static context
```

---

#### (c) 2 and 3 (Allowed)

**Example:**

```java
class Test {
    static int x = 10;

    public void methodOne() {
        System.out.println(x);
    }
}
```

**Output:**

```
Compiled successfully
```

---

#### (d) 2 and 4 (Allowed)

**Example:**

```java
class Test {
    static int x = 10;

    public static void methodOne() {
        System.out.println(x);
    }
}
```

**Output:**

```
Compiled successfully
```

---

#### (e) 1 and 2 (Not Allowed)

**Example:**

```java
class Test {
    int x = 10;
    static int x = 10;
}
```

**Output:**

```
Compile-time error:
x is already defined in Test
```

---

#### (f) 3 and 4 (Not Allowed)

**Example:**

```java
class Test {
    public void methodOne() {
        System.out.println(x);
    }

    public static void methodOne() {
        System.out.println(x);
    }
}
```

**Output:**

```
Compile-time error:
methodOne() is already defined in Test
```

---

### 4. Static and Abstract Methods

- Static methods must have implementation.
    
- Abstract methods do not have implementation.
    
- So, `static abstract` combination is **illegal** for methods.
    

---

### 5. Static Method Overloading

- Overloading is allowed for static methods, including `main` method.
    
- JVM always calls:
    
    ```java
    public static void main(String[] args)
    ```
    
- Other overloaded `main` methods are not called automatically.
    
- They must be called explicitly like normal methods.



![[Pasted image 20260131230438.png]]
![[Pasted image 20260131230547.png]]

### **Case 2: Inheritance and Static Methods (Notes)**

---

### 1. Inheritance and Static Methods

- Inheritance concept is applicable for **static methods**, including `main()` method.
    
- When a child class is executed:
    
    - If the child class **does not contain** `main()` method,
        
    - Then the **parent class main() method** will be executed.
        

---

### 2. Example

```java
class Parent {
    public static void main(String args[]) {
        System.out.println("parent main() method called");
    }
}

class Child extends Parent {
}
```

![[Pasted image 20260131230934.png]]

### Example 2:

![[Pasted image 20260131231030.png]]

![[Pasted image 20260131231221.png]]

---
## 📘 **Native Modifier**

- Native is a modifier applicable **only for methods**, not for variables and classes.
    
- Methods implemented in **non-Java languages** are called **native / foreign methods**.
    

### Objectives of `native` Keyword:

- To improve system performance.
    
- To use existing legacy non-Java code.
    
- To achieve machine-level communication (memory/address level).
    

### Declaration Rule:

- Native methods already have implementation.
    
- So, we **do not provide implementation** in Java.
    
- Hence, declaration must end with **semicolon (`;`)**.
    

**Example:**

- `public native void methodOne();` → ✅ Valid
    
- `public native void methodOne()` → ❌ Invalid
    

### Rules:

- `abstract native` combination is **illegal** because native have already implementation and abstract doesn't have implementation, child class needs to implement abstract methods.
    
- `native strictfp` combination is **illegal**.
    
- Inheritance, overriding, and overloading are applicable.
    

### Advantages:

- Performance improves.
    

### Disadvantages:

- Breaks platform-independent nature of Java.
    

---

## 📘 **Synchronized Modifier**

1. Applicable for **methods and blocks**, not for variables and classes.
    
2. At a time, **only one thread** can execute the synchronized method/block on an object.
    
3. Helps to solve **data inconsistency problems**.
    

### Advantages:

- Resolves data inconsistency.
    

### Disadvantages:

- Increases waiting time of threads.
    
- Affects system performance.
    
- Not recommended without specific requirement.
    

### Rule:

- Synchronized methods must have implementation.
    
- Abstract methods do not have implementation.
    
- So, `abstract synchronized` combination is **illegal**.
    

---

## 📘 **Transient Modifier**

1. Applicable **only for variables**, not for methods and classes.
    
2. Used when we **do not want to serialize** a variable (for security reasons).
    
3. During serialization, JVM saves **default value** for transient variables.
    
    - Meaning: _transient = not to serialize_.
        

### Important Points:

4. Static variables are not part of object state, so serialization does not apply.
    
    - Declaring static as transient has **no use**.
        
5. Final variables are serialized by their values.
    
    - Declaring final as transient has **no impact**.
        

---

## **4. Volatile Modifier**

### Volatile Keyword

- `volatile` is applicable **only for variables**.
    
- Not applicable to classes and methods.
    

---

### Purpose

- Used when variable value keeps changing.
    
- Helps in multithreading environment.
    

---

### Working

- JVM creates a separate local copy for each thread.
    
- All changes are made in local copy.
    
- Before thread ends, final value is updated in master copy.
    

---

### Advantages

- Solves data inconsistency problems.
    

---

### Disadvantages

- Increases complexity.
    
- Reduces performance.
    
- Almost outdated.
    
- Not recommended if not necessary.
    

---

### Restriction

- `final` + `volatile` is illegal.
    
- Final means constant.
    
- Volatile means changing.
    
- Both are opposite.
    

---
### **Declaration and Implementation of an Interface (Notes)**

---

### 1. Implementing an Interface

- When a class implements an interface, it must **provide implementation for all methods** of that interface.
    
- If the class does not implement all methods, then the class must be declared as **abstract**.
    
- In that case, the **child class** is responsible for providing implementation for remaining methods.
    

---

### 2. Access Modifier Rule

- While implementing interface methods, they must be declared as **public**.
    
- If they are not declared as `public`, it results in a **compile-time error**.
    

---
### Example:  
```java
interface Interf 
{ 
void methodOne(); 
void methodTwo(); 
} 
```
 
![[Pasted image 20260201000328.png]]



### Important Points

- Every concrete class must implement all interface methods.
    
- If methods are missing, class must be abstract.
    
- Child class must implement remaining methods.
    
- If not, compile-time error occurs.
    
- Compiler checks interface method implementation strictly.

### **Extends vs Implements (Notes)**

---

## 1. Class Extending a Class

- A class can **extend only one class** at a time.
    

**Example:**

```java
class One {
    public void methodOne() {
    }
}

class Two extends One {
}
```

---

## 2. Class Implementing Interfaces

- A class can **implement any number of interfaces** at a time.
    

**Example:**

```java
interface One {
    public void methodOne();
}

interface Two {
    public void methodTwo();
}

class Three implements One, Two {
    public void methodOne() {
    }

    public void methodTwo() {
    }
}
```

---

## 3. Class Extending a Class and Implementing Interfaces

- A class can **extend one class and implement any number of interfaces** at the same time.
    

**Example:**

```java
interface One {
    void methodOne();
}

class Two {
    public void methodTwo() {
    }
}

class Three extends Two implements One {
    public void methodOne() {
    }
}
```

---

## 4. Interface Extending Interfaces

- An interface can **extend any number of interfaces**.
    

**Example:**

```java
interface One {
    void methodOne();
}

interface Two {
    void methodTwo();
}

interface Three extends One, Two {
}
```

---

## 5. Multiple Choice Question

**Which of the following is true?**

1. A class can extend any number of classes. ❌
    
2. An interface can extend only one interface. ❌
    
3. A class can implement only one interface. ❌
    
4. A class can extend a class and implement an interface but not both together. ❌
    
5. An interface can implement any number of interfaces. ❌
    
6. None of the above. ✅
    

**Answer: 6**

---

## 6. Expression: X extends Y

**Question:** For which possibility of X and Y is this expression true?

Options:

1. Both are classes ❌
    
2. Both are interfaces ❌
    
3. Both can be classes or interfaces ✅
    
4. No restriction ❌
    

**Answer: 3**

---

## 7. Valid Combinations

### (a) `X extends Y, Z`

- X, Y, Z must be interfaces.
    

---

### (b) `X extends Y implements Z`

- X, Y must be classes.
    
- Z must be an interface.
    

---

### (c) `X implements Y, Z`

- X must be a class.
    
- Y, Z must be interfaces.
    

---

### (d) `X implements Y extends Z`

- This is **invalid syntax**.
    

---

## 8. Last Example (Error Case)

### Given Program

```java
interface One {
}

class Two {
}

class Three implements One extends Two {
}
```

---

### Output

```
Compile-time error:
'{' expected
```

---

## 9. Simple Explanation of Last Example

In Java:

- `extends` must come **before** `implements`.
    
- A class can:
    
    - Extend **one class**
        
    - Implement **interfaces**
        

Correct order is:

```
class ClassName extends ClassName implements InterfaceName
```

---

### ❌ Wrong Order (Given Example)

```java
class Three implements One extends Two {
}
```

Here:

- `implements` is written first.
    
- `extends` is written after it.
    
- This order is **not allowed in Java**.
    

So compiler gets confused and gives error.

---

### ✅ Correct Way

```java
class Three extends Two implements One {
}
```

Now:

- First extends class `Two`
    
- Then implements interface `One`
    
- This is valid.
    

---
