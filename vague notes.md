There is no concrete class which implements collection directly

> `Collection` itself has no concrete implementation because it is a generic abstraction.  
> The actual concrete classes are `ArrayList`, `HashSet`, `TreeSet`, etc., which implement the specific behavioral sub-interfaces of `Collection`.


>What you said (slightly cleaned up):
> - `Collection` is an interface
> - `List` and `Set` are interfaces
> - `ArrayList` and `HashSet` are concrete classes
> - `List` and `Set` extend `Collection`
> - `ArrayList` implements `List`, `HashSet` implements `Set`
> - `Collection` has generic methods like add, remove, etc.     
> - There is **no concrete class that implements `Collection` directly**

>Java does not provide any concrete class that implements Collection directly.  
  However, concrete classes like ArrayList and HashSet implement Collection indirectly through sub-interfaces such as List and Set.

>The object decides what exists;  
   the reference decides what you are allowed to use.


>Collection interface doesn’t contain any method to retrieve an object” — what does it mean?
    It means:
 👉 **`Collection` does NOT provide a method to access an element by index or position.**
  There is **no method like**:
 `get(int index)`
  in the `Collection` interface.
>Because **`Collection` is a very general interface**.
  > Some collections **do not have an order at all**, for example:
  >- `Set`
 > - `HashSet`
 >If there is **no fixed order**, then retrieving “the 3rd element” makes no sense.
 So Java designers **intentionally did not add** a `get()` method in `Collection`.

### Then how do we retrieve elements from a Collection?

There are **2 common ways**:

#### 1️⃣ Using **Iterator**

```java
Collection<String> c = new ArrayList<>(); 
c.add("A"); 
c.add("B");  
Iterator<String> it = c.iterator(); 
while (it.hasNext()) {     
System.out.println(it.next()); 
}
```

✔ Works for **all Collection types**

---
#### 2️⃣ Using **for-each loop**
```java
for (String s : c) 
{ 
    System.out.println(s); 
}
```

✔ Internally uses an iterator

---
### Then who provides `get(index)`?
👉 **`List` interface**, not `Collection`
```java
List<String> list = new ArrayList<>();
list.add("A");
list.add("B");
System.out.println(list.get(0)); // valid
```

>In array list heterogenous objects are allowed except treeset and treemap, because treeset and treemap sorts object and for sorting there is need for comparing objects. For object comparsion, the objects (let's say object x and object y) must be compulsorily homogenous.

>Inserting in the middle of an ArrayList shifts elements; a new internal array is created only if capacity is insufficient, not a new ArrayList object.

### “If capacity is 20 and I insert the 21st object, will it be possible?”
### ✅ YES, it is possible.
### What actually happens internally:
1️⃣ Current size = 20  
2️⃣ Capacity = 20  
3️⃣ You add the 21st element
👉 **ArrayList automatically grows**

---
## 1️⃣ `Serializable`

**What it means:**

> Objects of this class **can be converted into a byte stream** and saved/transmitted.

**Why needed:**

- Save object to file
    
- Send object over network
    
- Store object in DB / cache
    

**Example use-cases:**

- Session objects
    
- RMI
    
- File storage
    
```java

class Student implements Serializable {

    int id;

    String name;

}
```

⚠️ If a class **does NOT implement Serializable** → `NotSerializableException`

---

## 2️⃣ `Cloneable`

**What it means:**

> Objects of this class **can be cloned (copied)** using `clone()`.

**Important:**

- `clone()` method is in `Object` class
    
- But JVM checks **Cloneable marker** before allowing cloning
    
```java

class Employee implements Cloneable {

    protected Object clone() throws CloneNotSupportedException {

        return super.clone();

    }

}
```

⚠️ If Cloneable not implemented → `CloneNotSupportedException`

🧠 Default cloning = **shallow copy**

---

## 3️⃣ `RandomAccess`

**What it means:**

> Collection supports **fast (O(1)) index-based access**

Used mainly for **Lists**

**Examples:**

- ✅ `ArrayList` → implements RandomAccess
    
- ❌ `LinkedList` → does NOT

#note 
### Then who implements `Serializable`?

👉 ** Some Concrete collection classes**

Examples:

ArrayList     implements List, Serializable

LinkedList    implements List, Deque, Serializable

HashSet       implements Set, Serializable

HashMap       implements Map, Serializable

✔️ **Classes implement `Serializable`, not the `Collection` interface**

> ✅ **Some concrete collection classes implement `Cloneable`**

>` Treemap and Treeset don't implement cloneable`

#note 

### They do not implement serializable as well as collections
##### 🔹 **Wrapper collections (from `Collections` utility class)**
##### 🔹 **Concurrent collections (important)**
---
### 🔹 Program

- A **static thing**
    
- Just code stored on disk
    
- Example: `MyApp.java`, `MyApp.class`
    

> 🧠 A program is **not running**



### 🔹 Process

- A **running instance of a program**
    
- Has:
    
    - memory
        
    - heap
        
    - stack
        
    - OS resources
        

Example:

- Double-click Chrome → one **process**
    



### 🔹 Thread

- A **path of execution inside a process**
    
- Multiple threads can exist in one process
    

Example:

- One app → UI thread + background thread
    

An **execution path** means:

- **where execution starts**
    
- **which instruction runs next**
    
- **in what order instructions are executed**
    

Process (Java Application)
│
├── Thread-1 → executing method A → method B
│
├── Thread-2 → executing method X → method Y
│
└── Thread-3 → waiting / sleeping

In short:

> It’s the **flow of control** through the code.

Each thread has its own:

- **program counter** (which line to execute next)
    
- **call stack** (method calls)
    
- **local variables**
    

But threads **share**:

- heap memory
    
- objects
    
- static variables

### 📌 One-line summary ⭐

> **Program = code**  
> **Process = running program**  
> **Thread = execution path inside process**

---


## What synchronization guarantees (VERY IMPORTANT)

Synchronization gives **two guarantees**:

### ✅ 1. Mutual Exclusion

Only one thread executes critical section at a time
All other threads must **wait**
### ✅ 2. Memory Visibility

Changes made by one thread are **visible** to others

Without sync:

- threads may see **stale values**


## **Thread safety means:**  
No matter how many threads run concurrently, the program always behaves correctly.

