
---

## ✅ 1. What does `itt.next()` return?

You wrote:

```java
Iterator itt = ll.descendingIterator();
```

This is a **raw Iterator** (no generics).

So:

```java
itt.next()
```

returns:

```java
Object
```

👉 NOT `Practice`, only `Object`.

Because of this, the compiler only knows:

> “This is some Object. I don’t know which type.”

---

## ✅ 2. Why `.name` is NOT accessible?

When you do:

```java
String Name = (itt.next()).name;   // ❌ compile error
```

This fails because:

- `itt.next()` → returns `Object`
    
- `Object` class has **no field `name`**
    

So compiler says:

> ❌ Cannot find symbol: name

Even if **at runtime** the object is `Practice`,  
the compiler works at **compile time**, not runtime.

So it refuses.

---

## ✅ 3. Why casting works?

When you do:

```java
((Practice) itt.next()).author
```

You are telling compiler:

> "Trust me, this Object is a Practice."

Now compiler allows:

✔ `.author`  
✔ `.name`

Because `Practice` has those fields.

But ⚠️ Risk:

If the object is NOT `Practice` → `ClassCastException` at runtime.

---

## ✅ 4. BIG PROBLEM in Your Code (Very Important 🚨)

Your code calls `next()` MULTIPLE TIMES in one loop:

```java
System.out.println(itt.next());
System.out.println(((Practice)itt.next()).author);
itt.next().equals(itt);
String Name = (itt.next()).name;
```

Each `next()`:

👉 Moves iterator forward by 1

So in ONE loop iteration, you move 4 times 😨

Result:

- You skip elements
    
- You may get `NoSuchElementException`
    
- Logic breaks
    

This is WRONG practice.

---

## ✅ 5. Correct Way (Call `next()` Only Once per Loop)

Do this:

```java
Iterator<Practice> itt = ll.descendingIterator();

while (itt.hasNext()) {

    Practice p = itt.next();   // only once

    System.out.println(p);
    System.out.println(p.author);

    String name = p.name;
    System.out.println(name);
}
```

Now:

✔ No casting  
✔ No skipping  
✔ No runtime risk  
✔ Clean code

---

## ✅ 6. Why Generics Fix Everything?

Instead of:

```java
Iterator itt   // raw
```

Use:

```java
Iterator<Practice> itt
```

Then:

| Case             | Return Type |
| ---------------- | ----------- |
| Raw Iterator     | Object      |
| Generic Iterator | Practice    |

So:

```java
Practice p = itt.next(); // direct
```

No cast needed 🎯

---

## ✅ 7. Interview-Level Explanation (Remember This)

> ❓ Why `.name` not accessible on `itt.next()`?

Answer:

Because:

- Raw `Iterator` returns `Object`
    
- `Object` has no `name`
    
- Compiler checks at compile time
    
- Actual type is known only at runtime
    
- So casting is required
    

---

## 🔑 Final Answer to Your Question

> "Is it because compiler doesn't know actual type at compile time?"

👉 YES ✅ EXACTLY.

Because:

- You used raw `Iterator`
    
- So return type = `Object`
    
- Compiler has no idea it's `Practice`
    
- So `.name` is not allowed
    

---

## ⚠️ One More Best Practice (For You)

Always avoid raw types:

❌ Bad:

```java
Iterator itt
```

✅ Good:

```java
Iterator<Practice> itt
```

This is called **Type Safety**.

---
