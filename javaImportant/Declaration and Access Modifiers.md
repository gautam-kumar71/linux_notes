
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
