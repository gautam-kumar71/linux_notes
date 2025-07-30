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

- It holds the **address** of the object that invoked the member function or the constructor.
```cpp
#include <iostream>
using namespace std;
class Customer{
    string name;
    int accNO;
    int bal;

    public:
    // Without 'this', the function uses the constructor parameter instead of the member variable and this causes ambiguity.
    Customer(string name,int accNO,int bal)
    {
        this->name=name;
        this->accNO=accNO;
        this->bal=bal;
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
    Customer obj1("Kartik",1234,654);
    Customer obj2("Tara",34);
    obj1.getResult();
    obj2.getResult();
    return 0;
}
```

### INLINE CONSTRUCTOR
```cpp
#include<iostream>
using namespace std;
class Customer{
    string name;
    int accNo;
    int balance;
    public:
    inline Customer(string n,int a,int b):name(n),accNo(a),balance(b){
    } 
    //getter function
    void display(){
        cout<<name<<endl;
        cout<<accNo<<endl;
        cout<<balance<<endl;
    }
};
int main()
{
    Customer obj("Gautam",6184614,9466761);
    obj.display();
}
```

---
### 📝 **C++ Constructor Initializer List vs `this->` Usage**

#### ✅ **Correct Syntax for Member Initializer List**

```cpp
class Blueprint {
    string sky;
    int key;
    string water;
public:
    inline Blueprint(string sky, int key, string water)
        : sky(sky), key(key), water(water) {} // ✅
};
```

#### ❌ **Incorrect Syntax Using `this->`**

```cpp
inline Blueprint(string sky, int key, string water)
    : this->sky(sky), this->key(key), this->water(water) {} // ❌ Error
```

- **Error**: `this->` is **not allowed** in initializer lists.
    
- The initializer list automatically assumes the left-hand side refers to class members.
    

---

### 🔍 **Why It Works Without `this->`**

In this syntax:

```cpp
: sky(sky)
```

- **Left `sky`** refers to the class member
    
- **Right `sky`** refers to the constructor parameter
    

So the compiler assigns the constructor parameter to the member variable.

---

### ⚠️ **Ambiguity Inside Constructor Body**

```cpp
Blueprint(string sky, int key, string water) {
    sky = sky;         // ❌ Ambiguous, both refer to parameter
    this->sky = sky;   // ✅ Correct way to assign parameter to member inside body
}
```

---

### Copy Constructor
>**if you do not define a copy constructor**, the **compiler provides a 
>default copy constructor**. This constructor performs a **shallow copy**, meaning:
- It copies each **member variable** from one object to another.
- The default copy constructor performs a shallow copy.
  
```cpp
#include<iostream>
using namespace std;
class Customer{
    string name;
    int accNo;
    int balance;
    public:
    inline Customer(string n,int a,int b):name(n),accNo(a),balance(b){
    } 
    //getter function
    void display(){
        cout<<name<<endl;
        cout<<accNo<<endl;
        cout<<balance<<endl;
    }
};
int main()
{
    Customer obj1("Gautam",6184614,9466761);
    Customer obj2(obj1);// Default copy constructor is used
    obj2.display();
}
```

> If i explicitly make the copy constructor then the compiler won't create the default copy constructor. And if i don't use pass by reference , it will throw an error because it will call the copy constructor recursively.

```cpp
#include<iostream>
using namespace std;
class Customer{
    string name;
    int accNo;
    int balance;
    public:
    inline Customer(string n,int a,int b):name(n),accNo(a),balance(b){
    } 
    Customer(Customer &other)//if Customer(Customer other)--->it will throw error
    {
      name=other.name;
      accNo=other.accNo;
      balance=other.balance;
    }
    //getter function
    void display(){
        cout<<name<<endl;
        cout<<accNo<<endl;
        cout<<balance<<endl;
    }
};
int main()
{
    Customer obj1("Gautam",6184614,9466761);
    Customer obj2(obj1);
    obj2.display();
    //another way of copying
    Customer obj3;
    obj3=obj2;
    obj3.display();
}```
#note 
>If objects are passed by value instead of reference for copying without the default copy constructor present then it will lead to endless recursive calls and no object value will be 
>copied to other object's value.


![Diagram](important.jpg)

#note 
> Here's a catch:
> If you are trying to create a copy of an object like this:
> `classname Newobjectname;
> Newobjectname=previousobjectname;`
> In this case, it will throw error if there isn't any default constructor

```cpp
#include<iostream>
using namespace std;
class Blueprint{
  string sky;
  int key;
  string water;
  public:
   //Blueprint(){};//default Constructor
   inline Blueprint(){}
  //inline Blueprint():{} //can't declare like this ; //default constructor
  //initializer list can't be empty
  inline Blueprint(string sky,int key, string water):sky(sky),
   key(key),water(water){
   }
   //defining copy constructor
   Blueprint(Blueprint & originalobj){
	   sky=originalobj.sky;
	   key=originalobj.key;
	   water=originalobj.water;
   }
   void display()
   {
       cout<<sky<<" "<<key<<" "<<water<<endl;
   }
};

int main()
{
    Blueprint blue("blue",99,"green");
    Blueprint objBlue(blue);
    blue.display();   
    Blueprint objCopy;
    objCopy=blue;
    objCopy.display();
}```
