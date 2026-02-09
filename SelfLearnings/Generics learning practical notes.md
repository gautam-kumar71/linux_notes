
---

## ❌ Your Current Code

```java
class IntegerContainer<N> implements NumberContainer<Integer> {
```

You are saying:

👉 My class implements `NumberContainer<Integer>`

So Java thinks:

> "This class must work **only with Integer**."

But inside the class, you wrote:

```java
private N item;

public void add(N item)
public N get()
```

So now:

- Interface expects → `Integer`
    
- Class uses → `N` (generic)
    

⚠️ These two are **not the same**.

This creates a **type mismatch**.

---

## 🔴 Main Problem

Your interface is:

```java
interface NumberContainer<T extends Number> {
    void add(T item);
    T get();
}
```

So if you implement:

```java
implements NumberContainer<Integer>
```

Then Java expects:

```java
void add(Integer item);
Integer get();
```

But you wrote:

```java
void add(N item);   ❌
N get();           ❌
```

Mismatch ❗

---

## ✅ Rule: When You Fix a Generic Type, You Must Use It Everywhere

If you write:

```java
implements NumberContainer<Integer>
```

Then your class **must not be generic anymore**.

Correct version:

### ✔ Option 1: Only Integer (No Generics)

```java
class IntegerContainer implements NumberContainer<Integer> {

    private Integer item;

    @Override
    public void add(Integer item) {
        this.item = item;
    }

    @Override
    public Integer get() {
        return item;
    }

    public static void main(String args[]) {

        IntegerContainer intcont = new IntegerContainer();
        intcont.add(9);
        System.out.println(intcont.get());

    }
}
```

Here:

👉 Class is fixed to Integer only.

---

## ✅ Option 2: Fully Generic (Recommended)

If you want generics, do this:

```java
class IntegerContainer<N extends Number> implements NumberContainer<N>
```

Full code:

```java
class IntegerContainer<N extends Number> implements NumberContainer<N> {

    private N item;

    @Override
    public void add(N item) {
        this.item = item;
    }

    @Override
    public N get() {
        return item;
    }

}
```

And use it like:

```java
IntegerContainer<Integer> obj = new IntegerContainer<>();
IntegerContainer<Double> obj2 = new IntegerContainer<>();
```

👉 Works for all Numbers.

---

## 🧠 Easy Way to Remember

### ❓ Ask yourself:

> Am I fixing the type or keeping it flexible?

---

### If FIXED → No Generics

```java
implements NumberContainer<Integer>
```

❌ Don’t use `<N>`

---

### If FLEXIBLE → Use Same Generic Everywhere

```java
class X<N extends Number> implements NumberContainer<N>
```

✔ Same `N` everywhere

---

## 📌 Your Code Mixed Both (That’s the Error)

You mixed:

| Part      | Type    |
| --------- | ------- |
| Interface | Integer |
| Class     | N       |

❌ Conflict

---

## 🔹 Real-Life Example

Think like this:

```java
NumberContainer<Integer>
```

= "I only accept Integers"

But then you wrote:

```java
class <N>
```

= "I accept anything"

⚠️ Contradiction.

---

## ✅ Final Summary

Your mistake:

```java
implements NumberContainer<Integer>  // fixed type
class <N>                            // generic type
```

❌ Mixing fixed + generic

---

### Correct Ways

### ✔ Only Integer

```java
class IntegerContainer implements NumberContainer<Integer>
```

### ✔ Generic

```java
class IntegerContainer<N extends Number> implements NumberContainer<N>
```

---

