#### Getter and Setter

```cpp
#include<iostream>
using namespace std;
class Student
{
private:
string name;
int roll_no;
string standard;
//Getter and Setter
//setter
public:
void setRollno(int roll)
{
roll_no=roll;
}
void setStandard(string s)
{
standard=s;
}
void getRollno()
{
cout<<roll_no<<endl;
}
string getStandard(int pin)
{
if(pin==123)
return standard;
return "Enter correct pin to get standard";
}
};
int main()
{
Student s1;
s1.setRollno(71);
s1.setStandard("VIII B");
s1.getRollno();
string hold=s1.getStandard(56);
cout<<hold;
}
```

---

### 📌 Note::: vvvi homework: why empty class size is 1

---

### 📚 Padding Concept

> Padding refers to extra bytes inserted by the compiler between or after the data members of a class or struct  
> to ensure proper alignment in memory.  
> This alignment allows the CPU to access data more efficiently, improving performance.  
> By placing larger data types before smaller ones, we can often reduce or eliminate padding and save memory.

---

#### 📏 Alignment Rules

```
1 bytes ---> multiples of 1 [0,1,2,3,4...]
2 bytes ---> multiples of 2 [0,2,4,6,8...]
4 bytes ---> multiples of 4 [0,4,8,12,16...]
8 bytes ---> multiples of 8 [0,8,16,24,32...]
```

---

### 🧪 Padding Example 1 – No Padding

```cpp
#include<iostream>
using namespace std;
class Student
{
int a;
int b;
int c;
};
int main()
{
Student s1;
cout<<sizeof(s1);  //gives 12 bytes because all are like so no padding is used
}
```

---

### 🧪 Padding Example 2 – Padding due to `char`

```cpp
#include<iostream>
using namespace std;
class Student
{
int a;
char c;
};
int main()
{
Student s1;
cout<<sizeof(s1); //gives 8 bytes ; a a a a c but 5 is not divisible by the largest data elem ; so nearest possible number will be 8
}
```

---

### 🧪 Padding Example 3 – Padding in between

```cpp
#include<iostream>
using namespace std;
class Student
{
int a;
char c;
int b;
};
int main()
{
Student s1;
cout<<sizeof(s1); //gives 12 bytes ; a a a a c p p p b b b b 
}
```

---

### 🧪 Padding Example 4 – Mixed Types Optimized

```cpp
#include<iostream>
using namespace std;
class Student
{
char c;
char d;
int b;
double e;
};
int main()
{
Student s1;
cout<<sizeof(s1); //gives 16 bytes ; c c p p b b b b e e e e e e e e  
}
```

---

### 🧪 Padding Example 5 – Mixed Types Inefficient Order

```cpp
#include<iostream>
using namespace std;
class Student
{
char c;
int b;
char d;
double e;
};
int main()
{
Student s1;
cout<<sizeof(s1); //gives 24 bytes ; c p p p b b b b d p p p p p p p e e e e e e e e  
}
```

---

### STATIC VS DYNAMIC MEMORY ALLOCATION

**#Note:** 
> Objects can be created dynamically too.  

In **dynamic memory allocation**, objects can take more space compared to static memory allocation.  
This is achieved using **pointers**.
- **Static memory allocation** uses the **stack**.
- **Dynamic memory allocation** uses the **heap**.

```cpp
Classname *objName=new Classname;
(*objName).propertyname=value;

or

objName->propertyname = value; 
```

# Constructor and Destructor
- It is a special function that is invoked automatically at the time of object creation
- Name of the constructor should be same as the class name
- It doesn't have any return type
- It is used to initialize the value
- **All members and constructors** in a class are `private` by default unless specified otherwise.
- What does this do? This object stores the created object's address
 #note
 >💡 **In C++, once you write an _access specifier_ like `public:`, everything after that (until another access specifier like `private:` or `protected:`) will be treated with that access level.**
---
### 🧪Example 1
``` cpp
#include <iostream>
using namespace std;
class Customer{
    string name;
    int accNO;
    int bal;
    
    //all members and constructors in a class are by default "private"
    //so explicitly we have to make it public
    //Default Constructor
    public:
    Customer(){
        cout<<"Hello this is me from default constructor";
    }
};


int main() {
    Customer obj;
    return 0;
}
```
### 🧪Example 2
```cpp
#include <iostream>
using namespace std;
class Customer{
    string name;
    int accNO;
    int bal;

    public:
    Customer(){
        name="aman";
        accNO=123;
        bal=654;
    }
    //getter function
    void getResult()
    {
        cout<<name<<endl;
    }
    
};
int main() {
    Customer obj;
    obj.getResult();
    return 0;
}
```
---
### 🧪Example 3
```cpp
#include <iostream>
using namespace std;
class Customer{
    string name;
    int accNO;
    int bal;

    public:
    Customer(){
        name="aman";
        accNO=123;
        bal=654;
    }
    //parameterizd constructor
    Customer(string n,int a,int b)
    {
        name=n;
        accNO=a;
        bal=b;
    }
    //getter function
    void getResult()
    {
        cout<<name<<endl;
        cout<<accNO<<endl;
        cout<<bal<<endl;
    }
};


int main() {
    Customer obj;
    Customer obj2("Kartik",1234,654);
    obj.getResult();
    obj2.getResult();
    return 0;
}
```

#note 

> “If you declare a constructor yourself, then the compiler won't generate a default constructor.”
---
> ❗ **Note:** If you define any constructor yourself (e.g., a parameterized one), the **compiler will not automatically generate a default constructor**.  
> You must explicitly define the default constructor if you need one.

---
### Example:

```cpp
class MyClass {
public:
    MyClass(int x) { }  // Custom constructor

    // Now this won't work unless you add:
    // MyClass() {}  // Manually define default constructor
};

MyClass obj;  // ❌ Error: no matching default constructor
```

### Constructor overloading
**Constructor overloading** in C++ is the ability to define **multiple constructors** in the same class, with the **same name** (the class name), but with **different numbers or types of parameters**.

- All constructors must have **unique parameter types or counts**.
- The compiler figures out which constructor to call based on the arguments you pass.
- The compiler uses the **number** and **types** (and **order**) of parameters to distinguish between overloaded constructors.

```cpp
#include <iostream>
using namespace std;
class Customer{
    string name;
    int accNO;
    int bal;

    public:
    Customer(){
        name="aman";
        accNO=123;
        bal=654;
    }
    //parameterizd constructor
    Customer(string n,int a,int b)
    {
        name=n;
        accNO=a;
        bal=b;
    }
    Customer(string n,int a)
    {
        name=n;
        accNO=a;
    }
    //getter function
    void getResult()
    {
        cout<<name<<endl;
        cout<<accNO<<endl;
        cout<<bal<<endl;
    }
};


int main() {
    Customer obj;
    Customer obj2("Kartik",1234,654);
    Customer obj3("Tara",34);
    obj.getResult();
    obj2.getResult();
    obj3.getResult();
    return 0;
}
```

#note 
> `this` is an implicit pointer available inside **non-static member functions** of a class or struct , and it points to the object that invoked the method.

- It holds the **address** of the object on which the function (constructor or method) is being called.
    
- Inside a constructor, `this` refers to the object that is being **constructed**.
    
- Inside a member function, it refers to the object that **called** the function.