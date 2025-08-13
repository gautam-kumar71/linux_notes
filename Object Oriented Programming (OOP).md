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
- What does "this" do? "This" object stores the created object's address
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
}
```



---
#note 
>If objects are passed by value instead of reference for copying without the default copy constructor present then it will lead to endless recursive calls and no object value will be 
>copied to other object's value.


![Diagram](important.jpg)


#note 
> Here's a catch:
> If you are trying to create a copy of an object like this:
> `classname Newobjectname;`
> `NewObjectName=PreviousObjectName;`
> and not like this:
> `Blueprint objBlue(blue);`
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
   Blueprint(Blueprint &originalobj){
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
    Blueprint objCopy;// mainly throws an error if there isn't any default constructor
    objCopy=blue;
    objCopy.display();
}
```

## Destructor
- Has **no return type**
- Has **no parameters**
- It is an instance member function that is invoked automatically whenever an object is going to be destroyed
- It is the last function that is going to be called before an object is destroyed.
-  **You can only define **one** destructor per class**
   It looks like: `~Customer() { ... }`
   But...other destructors (member objects, base classes) are always involved
   You don't write them, but the compiler will still call them **automatically**, **after** your destructor runs.
>Constructor is called orderwise but destructor is called reverse wise.
```cpp
#include<iostream>
using namespace std;
class Customer{
 string name;
 int *data;
 public:
  Customer(string name)
  {
     this->name=name;
     cout<<"From constructor section:"<<name<<endl;
  }
  ~Customer()
  {
      cout<<"Destructor is being called:"<<name<<endl;
  }
};
int main(){
Customer A1("1"),A2("2"),A3("3");
}
```

  
```cpp
#include<iostream>
using namespace std;
class Customer{
   string name;
   int *data;
   public:
    Customer()
    {
      name="Gautam";
	  data=new int;
	  *data=10;
	  cout<<"successfully the constructor has been created"<<endl;
    }
    ~Customer()
    {
      delete data;//delete name does'nt work because it isn't dynamically alloted
	  cout<<"destructor is called"<<endl;
    }
};
int main()
{
  Customer A1;
}
```
#note 
- Each class can have **only one** custom destructor(can't overload a destructor like constructor)
- eg:
```cpp
   ~MyClass();         // ✅ Allowed
   ~MyClass(int x);    // ❌ Error: Destructor cannot be overloaded
```
## ⚙️ **Destructor Execution Order**

### 🔄 When an object is destroyed:

1. Your class’s **destructor** (`~YourClass`) is called
    
2. Then **member objects’ destructors** are called (like `std::string`)
    
3. Then **base class destructors** (if any)
    
4. Then the **object's memory is released**

**Its job is to**:
1. **Clean up resources** that the object used during its lifetime. It doesn't remove the object.
    
2. That includes:
    
    - Dynamically allocated memory (`new`)
        
    - Open file handles
        
    - Network connections
        
    - Locks, mutexes
        
    - Database connections
        
    - And anything else that needs cleanup

```cpp
#include<iostream>
using namespace std;
class Customer{
 string name;
 int *data;
 public:
 //default constructor
 Customer()
 {
	 name="4";
	 cout<<"From the newly created constructor:"<<name<<endl;
 }
 Customer(string name)
  {
     this->name=name;
     cout<<"From constructor section:"<<name<<endl;
  }
  ~Customer()
  {
      cout<<"Destructor is being called:"<<name<<endl;
  }
};
int main(){
Customer A1("1"),A2("2"),A3("3");
Customer *A4=new Customer();
delete A4;//explicitly delete the A4 pointer to a heap
}
```

### 💣 If You Skip `delete A4`:

If you remove or comment out `delete A4;`, the destructor **won’t be called automatically**, because:

- `A4` is a pointer to an object on the **heap**.
    
- Objects created with `new` **must be deleted manually**.
    
- Otherwise, the memory remains allocated (→ **memory leak**) and the destructor is **never called**.

#note:
Why destructors are called in reverse order?
- Because the earlier objects might be dependent on next objects , so it is safe to delete the last ones first

## Static Data Member

- They are attribute of classes or class member.  
- It is declared using static keyword .
- Only one copy of that member is created for the entire class & is shared by all the object. 
- It is initialized before any object of this class is created.

```cpp
#include<iostream>
using namespace std;
class Accounts{
   string name;
    int acNo;
    int age;
    public:
    static int totalCustomers;
public:
    inline Accounts(string n,int a, int ag):name(n),acNo(a),age(ag){totalCustomers++;}
    void display()
    {
	cout<<name<<endl;
    cout<<acNo<<endl;
	cout<<age<<endl;
	cout<<totalCustomers<<endl;
    }
};
int Accounts::totalCustomers=0;
int main()
{
    Accounts a1("Gautam",69664616,22);
    a1.display();
    Accounts a2("Gautam",69664616,22);
    a2.display();
    Accounts a3("Gautam",69664616,22);
    a3.display();
    Accounts a4("Gautam",69664616,22);
    a4.display();
    Accounts a5("Gautam",69664616,22);
    a5.display();
    Accounts a6("Gautam",69664616,22);
    a6.display();
    Accounts a7("Gautam",69664616,22);
    a7.display();
    Accounts::totalCustomers=10;//to access directly without creating any object
    a7.display();
}
```


