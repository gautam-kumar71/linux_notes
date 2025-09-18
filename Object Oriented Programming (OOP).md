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
// The size of a struct/class must be a multiple of the largest member alignment requirement.
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
- It is a  non-static special function that is invoked automatically at the time of object creation
- Name of the constructor should be same as the class name
- It doesn't have any return type
- It is used to initialize the value
- **All members and constructors** in a class are `private` by default unless specified otherwise.

#vvi
### ✅ What `this` really is
- `this` is an **implicit pointer** that exists inside all non-static member functions.
- It always points to the **calling object** (the object that invoked the function).
-  It **does not** point to a newly created object or a result object.
---
### ❌ Misconception

> _“`this` object stores the created object’s address.”_  
> That’s **wrong** because:
> 
- `this` only points to the object that the function was called on.

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
> `this` is an implicit pointer available inside **non-static member functions** of a class or struct , and it points to the object that invoked/called the method.

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
`
`An initializer list is the part of a constructor, written after a colon (`:`), that initializes member variables before the constructor body runs.`

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
    obj3=obj2;//it is not using the custom copy constructor rather it uses 
              //copy assignment operator
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
-  Derived class destructor is called first and then Parent class destructor is called afterwards.(applies to all type of inheritance) 
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

# Static Member Function
- It can be accessed without the creation of objects
- it can only access static variables
- To access a static function all you need to do is:

```cpp
   classname::staticFunctionName();
```

# Static Member Function example
```cpp
#include<iostream>
using namespace std;
class Accounts{
   string name;
    int acNo;
    int balance;
    static int totalCustomers;
    static int totalBalance;
    public:
    inline Accounts(string n,int a, int b):name(n),acNo(a),balance(b)
    {
	totalBalance+=balance;
	totalCustomers++;
    }
    void deposit(int amount)
    {
	if(amount>0)
	{
	 balance+=amount;
	 totalBalance+=amount;
      }
    }

    void withdraw(int amount)
    {
	if(amount>0&&balance>=amount)
         {
     	   balance-=amount; 
	   totalBalance-=amount;
         }
    }
    void display()
    {
	cout<<"Name="<<name<<endl;
        cout<<"Account no="<<acNo<<endl;
        cout<<"balance="<<balance<<endl;
	cout<<"totalBalance="<<totalBalance<<endl;
	cout<<"totalCustomers="<<totalCustomers<<endl;
    }
    //static member function
    //can access only static variables even if it's private
    static void acceStatic()
     {
       cout<<totalCustomers<<endl;
     }
};
int Accounts::totalCustomers=0;
int Accounts::totalBalance=0;
int main()
{
    Accounts a1("Gautam",69664616,2000);  
    Accounts a2("Gautam",69664616,1200);
    Accounts a3("Gautam",69664616,4200);
    a3.deposit(600);
    a3.withdraw(7000);
    a3.display();
    Accounts::acceStatic();
}
```

#note: homework - const keyword
# Encapsulation

- Wrapping up of data and functions into a single unit while controlling access to them.
- Functions and variables are encapsulated together in a single capsule (class).
- Variables are usually declared **private**, and functions are usually declared **public**.
- It enables **data hiding** and provides controlled access through methods.
- The primary goal of encapsulation is to avoid the data to be accessed directly so that the user doesn't end up in changing the values of the variables directly.
 
 #Example  
  If the variable `age` is declared **public**, it can be accessed and modified directly. Suppose a user sets the value of `age` to **-5**, which is not valid since age should always be positive. Because the variable is public, such invalid values can be assigned, leading to faulty or inconsistent data.  
  To prevent this, the variable is declared **private**, and member functions (getters and setters) are created to validate the input. For instance, the setter function can check whether the new value of `age` is positive before applying the change.

 👉 This makes it clear how **encapsulation enables data hiding and validation**.

```cpp
#include<iostream>
using namespace std;
class Accounts{
   public: ❌❌❌//shouldn't be declared public here
    string name;
    int acNo;
    int balance;
    static int totalCustomers;
    static int totalBalance;
    public:
    inline Accounts(string n,int a, int b):name(n),acNo(a),balance(b)
    {
      if(balance<0)
      throw invalid_argument("Balance Can't be negative");
	  totalBalance+=balance;
	  totalCustomers++;
    }
    void deposit(int amount)
    {
	if(amount>0)
	 {
	   balance+=amount;
	   totalBalance+=amount;
     }
    }

    void withdraw(int amount)
    {
	if(amount>0&&balance>=amount)
         {
     	   balance-=amount; 
	       totalBalance-=amount;
         }
    }
    void display()
    {
	cout<<"Name="<<name<<endl;
    cout<<"Account no="<<acNo<<endl;
    cout<<"balance="<<balance<<endl;
	cout<<"totalBalance="<<totalBalance<<endl;
	cout<<"totalCustomers="<<totalCustomers<<endl;
    }
    //static member function
    //can access only static variables even if it's private
    static void acceStatic()
     {
       cout<<totalCustomers<<endl;
     }
};
int Accounts::totalCustomers=0;
int Accounts::totalBalance=0;
int main()
{
    Accounts a1("Gautam",69664616,2000);//Here,it works fine,bcz balance is +ve
    a1.balance=-10;❌❌❌ //can be changed directly,should be strictly avoided
    a1.display();
    Accounts::acceStatic();
}
```

# Abstraction
- Displaying only the essential information and hiding the details.
#Example:
Suppose a person wants to ride a bike. They do not need to know about the internal workings of the bike; they can simply focus on riding it. This is abstraction.

#Example2:
In the above code we don't need to know exactly how this codebase is handling withdraw function.

# Inheritance

- The capability of a class to derive properties and characteristics from another class is called **Inheritance**.
- The class from which properties are derived is called the **base class (or parent class)**, and the class that derives these properties is called the **derived class (or child class)**.

| Access Specifier | External Code | Within Class | Derived Class |
|------------------|---------------|--------------|---------------|
| Public           | ✔             | ✔            | ✔             |
| Protected        | ✘             | ✔            | ✔             |
| Private          | ✘             | ✔            | ✘             |
#important
`Rule of thumb:`
`private(very strict) > protected(less strict) > public(not strict)`


| Base Class Member Access Specifier | Public Inheritance      | Protected Inheritance   | Private Inheritance     |
| ---------------------------------- | ----------------------- | ----------------------- | ----------------------- |
| Public                             | Public                  | Protected               | Private                 |
| Protected                          | Protected               | Protected               | Private                 |
| Private                            | Not accessible (Hidden) | Not accessible (Hidden) | Not accessible (Hidden) |

![[diagram1.png]]

![[diagram2.png]]

![[diagram3.png]]

```cpp
#include<iostream>
using namespace std;
class Human{
   public:
     string name;
     int age;
};

//defining a child class
//Syntax:
//class childClassName:accessSpecifier ParentClassName
class Student1:public Human{
    public:
    int rollNumber;
};
class Student2:protected Human{
   char bloodGroup;
   public:
    void setName(string name)
    {
        this->name=name;
    }
    void display()
    {
        cout<<"Name is accessible in the derived class:"<<name<<endl;
    }
};
class Student3:private Human{
    int phNo;
};
int main()
{
    //obj1
    Student1 s1;
    s1.rollNumber=12;
    cout<<s1.rollNumber<<endl;
  
    //obj2
    Student2 s2;
    // s2.bloodGroup='b';//can't be accessed 
    // s2.name="Gautam";//can't be accessed because it's protected now
    s2.setName("Gautam");
    s2.display();
    
    //obj3
    Student3 s3;
    // s3.bloodGroup='b';//can't be accessed because it's private now
    
}
```
# Types of Inheritance
### 1. Single Inheritance
  - Single inheritance occurs when **a derived class inherits from only one base class**.
#### **Key Points**

1. **Constructors:**
    
    - Base class constructor is called **first**, then derived class constructor.
        
    - Syntax to call parameterized base constructor:
        
    
    `Derived(int x) : Base(x) {}`
    
2. **Destructors:**
    
    - Derived class destructor is called **first**, then base class destructor.
        
    - If using pointers, make **base destructor virtual** for proper cleanup.
        
3. **Method Overriding:**
    
    - Derived class can **override** base class methods.
        
    - If base method is **virtual**, derived method is called through base pointer.
```cpp
#include<iostream>
using namespace std;

//Base class
class Human{
    protected:
     string name;
     int age;
    public:
    void work()
    {
     cout<<"I'm working\n"; 
    }
    //First the parent class constructor is called and then the child class's          constructor is called
    Human()
    {
        cout<<"Hello Human"<<endl;
    }

    //constructor for initializing values
    //This is being called from the child class
    Human(string name,int age)
    {
      (*this).name=name;
      this->age=age;
    }

    
    void display()
    {
        cout<<name<<" "<<age<<endl;
    }
    
    ~Human(){
        cout<<"Destructor of human is being called second"<<endl;
    }
};

//Inheriting class (derived class)
class Student:public Human{
    int roll_number,fees;
    public:
    // Student(string name,int age,int roll_number,int fees)
    // {
    //     this->name=name;
    //     this->age=age;
    //     this->roll_number=roll_number;
    //     this->fees=fees;
    // }
    
    Student(string name,int age,int roll_number,int fees):Human(name,age)
    {
        this->roll_number=roll_number;
        this->fees=fees;
    }
    
    
    // Both the class have the same method name as "display"
    // Now, between both of the two, the class whose object is being
    // created will be called first.
    // Here, student object is being created,so the "display" method
    // of student will be called
    
    void display()
    {
        cout<<name<<" "<<age<<" "<<roll_number<<" "<<fees<<endl;
    }
    
    ~Student(){
        cout<<"Destructor of student is being called first"<<endl;
    }
    
};

int main()
{
   Student s1("Gautam",22,166,77969);
   s1.work();
   s1.display();
}
```

### 2. Multilevel Inheritance
- Multilevel inheritance occurs when **a class is derived from a derived class**, forming a “chain” of inheritance.
#### **Key Points**
1. **Constructor Order:**
    
    - Base class constructor → Intermediate derived class constructor → Most derived class constructor.
        
2. **Destructor Order:**
    
    - Most derived class destructor → Intermediate derived class destructor → Base class destructor.
        
3. **Access Specifiers:**
    
    - Follows the same rules as single inheritance.
        
    - `protected` members of base are accessible in all derived classes.
        
    - `private` members of base are **not directly accessible**.
        
4. **Method Overriding:**
    
    - A derived class can **override** methods of any base class.
        
    - Use `virtual` in the base class for proper polymorphic behavior.

![[Multilevel-inheritence2.webp]]

```cpp
#include<iostream>
using namespace std;

class Person{
    protected:
    string name;
    
    public:
    void introduce()
    {
        cout<<"This is me, a person whose name is: "<<name<<endl;
    }
};

class Employee:public Person{
   protected:
   int salary;
   
   public:
   void monthlySalary()
   {
       cout<<"Monthly Salary: "<<salary<<endl;
   }
};

class Manager:public Employee{
  public:
  string department;
  Manager(string name,int salary,string department){
      this->name=name;
      this->salary=salary;
      this->department=department;
  }
  void work()
  {
      cout<<"I am leading the department "<<department<<endl;
  }
};

int main()
{
    Manager m1("Gautam",246136,"IT");
    m1.work();  
    m1.monthlySalary();
    m1.introduce();
}
```

#### 3. Multiple Inheritance
- Multiple inheritance occurs when **a derived class inherits from more than one base class**
- one child has multiple parents.

![[inheritence3.webp]]

#### **Key Points**

1. **Access Specifiers:**
    
    - Public/protected/private rules apply **for each base class individually**.
        
    - Private members of a base class are **not directly accessible** in the derived class.
        
2. **Constructor Order:**
    
    - Base1 constructor → Base2 constructor → Derived class constructor
        
3. **Destructor Order:**
    
    - Derived destructor → Base2 destructor → Base1 destructor
        
4. **Diamond Problem:**
    
    - If two base classes inherit from the same class, ambiguity occurs.
        
    - Solve using **virtual inheritance**.
        
5. **Method Overriding:**
    
    - Derived class can override methods from any base class.
        
    - If same method exists in multiple base classes, **scope resolution** is needed.


```cpp
#include<iostream>
using namespace std;

class Engineer{
    protected:
    string spec;
    
    public:
    inline Engineer(){
        cout<<"Engineer is called first"<<endl;
    }
    void work()
    {
        cout<<"I have specializtion in : "<<spec<<endl;
    }
};

class Youtuber{
   
   public:
   int subscribers;
   inline Youtuber(){
        cout<<"Youtuber is called second"<<endl;
    }
   void contentCreator()
   {
       cout<<"I have a subscriber base of "<<subscribers<<endl;
   }
};

class codeTeacher:public Engineer,public Youtuber{
  public:
  string name;
  inline codeTeacher(){
        cout<<"codeTeacher is called third"<<endl;
    }
  codeTeacher(string name,string spec, int subscribers)
  {
      this->name=name;
      this->spec=spec;
      this->subscribers=subscribers;
  }
  void showCase()
  {
      cout<<"My name is: "<<name<<endl;
      work();
      contentCreator();
  }
};

int main()
{
    // codeTeacher ct;
    codeTeacher ct("Gautam","AIML",618461464);
    ct.showCase();  
    
}

```

### Hierachial Inheritance

- Hierarchical inheritance occurs when **multiple derived classes inherit from the same base class**. 
- One parent has many children

![[hierachicalInheritance.png]]

```cpp
#include<iostream>
using namespace std;

class Human{
    protected:
     string name;
     int age;
    public:
     Human()
      {
        cout<<"Hello Human from the human constructor"<<endl;
      }
     Human(string name,int age)
      {
        (*this).name=name;
        this->age=age;
      }

    void display()
    {
        cout<<name<<" "<<age<<endl;
    }
    
    ~Human()
    {
        cout<<"Destructor of human is being called "<<endl;
    }
};

//Inheriting class (derived class)
class Student:public Human{
    int roll_number,fees;
    public:
    Student(string name,int age,int roll_number,int fees):Human(name,age)
    {
        this->roll_number=roll_number;
        this->fees=fees;
    }
    
    void display()
    {
        cout<<name<<" "<<age<<" "<<roll_number<<" "<<fees<<endl;
    }
    
    ~Student()
    {
        cout<<"Destructor of student is being called "<<endl;
    }
};

class Teacher:public Human
{
    int salary;
    public:
    Teacher(int salary,string name,int age)
    {
        this->salary=salary;
        this->name=name;
        this->age=age;
    }
    
    void display()
    {
        cout<<name<<" "<<age<<" "<<salary<<endl;
    }
    
    ~Teacher()
    {
        cout<<"Destructor of teacher is being called "<<endl;
    }
};

int main()
{
   Student s1("Gautam",22,166,77969);
   s1.display();
   Teacher t(99,"pinky",28);
   t.display();
}
```

### ⚠️ Key Takeaways:
- **For Teacher:** default Human() constructor was called → later Teacher destructor + Human destructor executed.
    
- **For Student:** parameterized Human(name, age) constructor was called → later Student destructor + Human destructor executed.
    

---

### ⚠️ Key Learning Points:

1. **If you don’t explicitly call a base constructor in the initializer list, the compiler automatically calls the default constructor of the base.**  
    (That’s why Teacher used Human()).
    
2. **Destructors are called in reverse order:**
     (this applies to all the types of inheritance)
    - First derived class destructor
        
    - Then base class destructor
#note 
Teacher and Student are children of the Human parent class.  
When a Student object goes out of scope, its destructor is called first, followed by the destructor of the Human class.
Similarly, when a Teacher object goes out of scope, its destructor is called first, followed by the destructor of its parent class, Human.  

### Hybrid Inheritance

**Hybrid inheritance** is a **combination of two or more types of inheritance**.  
It usually mixes:
- **Hierarchical inheritance** (one base, many children)
- **Multiple inheritance** (a class inherits from more than one base).
👉 In C++, hybrid inheritance often leads to the **Diamond Problem** (if two parent classes inherit from the same base class). That’s where **virtual inheritance** comes in.

![[hybridInheritance.png]]

```cpp
#include <iostream>
using namespace std;
#define e endl

class Student {
protected:
    string name;
    int rollNumber;
    string gender;

    // defining the student constructor
    Student(string name, int rollNumber, string gender) {
        this->name = name;
        this->rollNumber = rollNumber;
        this->gender = gender;
        cout << "Student constructor being called" << e;
    }

    ~Student() {
        cout << "Getting called from the student destructor" << e;
    }
};

class Male {
protected:
    string voice;
    bool masculinity;
    string hairs;

public:
    Male(string voice, bool masculinity, string hairs) {
        this->voice = voice;
        this->masculinity = masculinity;
        this->hairs = hairs;
        cout << "Male constructor is being called" << e;
    }

    ~Male() {
        cout << "Getting called from the male destructor" << e;
    }
};

class Female {
protected:
    string voice;
    bool feminity;
    string hairs;

public:
    inline Female(string voice, bool feminity, string hairs)
        : voice(voice), feminity(feminity), hairs(hairs) {
        cout << "Female constructor is being called" << e;
    }

    ~Female() {
        cout << "Getting called from the female destructor" << e;
    }
};

class Boy : public Student, public Male {
protected:
    string dress;

public:
    Boy(string name, int roll, string gender,
        string voice, bool masc, string hairs, string dress)
        : Student(name, roll, gender), Male(voice, masc, hairs) {
        this->dress = dress;
        cout << "Boy constructor called" << e;
        cout << name << " " << roll << " " << gender << " "
             << voice << " " << masc << " " << hairs << " "
             << dress << e;
    }

    ~Boy() {
        cout << "Calling the destructor of the Boy " << e;
    }
};

class Girl : public Student, public Female {
protected:
    string dress;

public:
    Girl(string name, int roll, string gender,
         string voice, bool femi, string hairs, string dress)
        : Student(name, roll, gender), Female(voice, femi, hairs) {
        this->dress = dress;
        cout << "Girl constructor being called" << e;
        cout << name << " " << roll << " " << gender << " "
             << voice << " " << femi << " " << hairs << " "
             << dress << e;
    }

    ~Girl() {
        cout << "Calling the destructor of the Girl " << e;
    }
};

int main() {
    Boy b1("Gautam", 12, "male", "deep", true, "short", "shirt-pant");
    Girl g1("Sumitra", 19, "female", "soft-pitched", true, "long","topNskirt");
}
```

### Multipath Inheritance

- Multipath inheritance is a type of inheritance in **OOP (Object-Oriented Programming)** where a class is derived from two different classes, and **both parent classes have a common base class**.
-  **Problem**: Ambiguity (multiple copies of the same base).
- **Solution**: Use **virtual inheritance** in C++.

![[multiPath.png]]

```cpp
#include<iostream>
using namespace std;

class Human{
    public:
    string name;
    void display(){
        cout<<"My name is :"<<name<<endl;
    }    
};

class Engineer:public virtual Human{
    protected:
    string spec;
    
    public:

    void work()
    {
        cout<<"I have specializtion in : "<<spec<<endl;
    }
};

class Youtuber:public virtual Human{
   
   public:
   int subscribers;
   
   void contentCreator()
   {
       cout<<"I have a subscriber base of "<<subscribers<<endl;
   }
};

class codeTeacher:public Engineer,public Youtuber{
  public:
  int salary;
  codeTeacher(string name,string spec, int subscribers,int salary)
  {
      this->name=name;
      this->spec=spec;
      this->subscribers=subscribers;
      this->salary=salary;
  }
  
};

int main()
{
    codeTeacher ct("Gautam","AIML",618461464,99);
    ct.display();
}
```

Good question 👍 Let’s carefully break this down.

It depends **how the inheritance is structured** and **where the method is coming from**.

---

### Case 1: **Two parent classes have same method, child does not override**

```cpp
#include <iostream>
using namespace std;

class A {
public:
    void show() { cout << "A::show()" << endl; }
};

class B {
public:
    void show() { cout << "B::show()" << endl; }
};

class C : public A, public B { };

int main() {
    C obj;
    // obj.show();   // ❌ Ambiguity: compiler doesn’t know A::show() or B::show()
    obj.A::show();   // ✅ Calls A’s version
    obj.B::show();   // ✅ Calls B’s version
}
```

👉 If **both parents have the same function name**, the child must **disambiguate** (you must specify `A::` or `B::`).  
It’s **not automatic** — compiler won’t just pick one.

---

### Case 2: **Child overrides the method**

```cpp
class C : public A, public B {
public:
    void show() { cout << "C::show()" << endl; }
};

int main() {
    C obj;
    obj.show();   // ✅ C::show() (child overrides everything)
}
```


---
#Question. #DOUBT
Will look after sometime  after overriding is done then
But ig if two classes have same method name, and the one which we are creating oject of gets called first right?

✅ **So to answer your doubt:**
- If **multiple inheritance** → compiler says _ambiguous_, you must specify `Parent::method`.
- If **single path inheritance** → the **nearest class in hierarchy** wins.
- If **child overrides** → the child’s method is always used.

### POLYMORPHISM

The word ****polymorphism**** means having many forms. A real-life example of polymorphism is a person who at the same time can have different characteristics.

In C++, polymorphism concept can be applied to functions and operators. A single function can work differently in different situations. Similarly, an operator works different when used in different context.
#### Compile Time Polymorphism
Also known as ****early binding**** and ****static polymorphism****, in compile-time polymorphism, the compiler determines how the function or operator will work depending on the context. This type of polymorphism is achieved by function overloading or operator overloading.
##### 1. Function Overloading

Function overloading is a feature in C++ (and some other languages) that allows you to **have multiple functions with the same name but different parameters** in the same scope. The compiler decides which function to call based on **the number or types of arguments** you pass.

### Key Points:

-  **Same function name**: All the overloaded functions share the same name.
-  **Different parameters**: The functions must differ in at least one of these:
    - Number of parameters        
    - Type of parameters
    - Order of parameters (if types are different)
-  **Return type does NOT matter**: You cannot overload a function based only on return type.

```cpp
#include <iostream>
using namespace std;

class Area
{
public:
    // Function to calculate area of a circle
    double calculateArea(int r)
    {
        return 3.14 * r * r;
    }

    // Function to calculate area of a rectangle
    int calculateArea(int l, int b)
    {
        return l * b;
    }
};

int main()
{
    Area A1, A2;

    double circleArea = A1.calculateArea(4);
    int rectangleArea = A2.calculateArea(3, 1);

    cout << "Area of circle with radius 4: " << circleArea << endl;
    cout << "Area of rectangle 3x1: " << rectangleArea << endl;
    return 0;
}
```

#note:

 -  Even though you changed the return type for the circle version to `double`, it **does not affect  overloading**—overloading depends only on **parameters**, not return type.
 - Rearranging same parameters with the same signature is still the same. 
    So, the compiler will treat it as identical function.(either change the type or number of params)
 
 ```cpp
 int calculateArea(int l, int b)
   {
     return l * b;
   }

 int calculateArea(int b, int l)
   {
    return l + b;  
   }
```
--- 
###  2. _Operator Overloading_
C++ has the ability to provide the operators with a special meaning for particular data type, this ability is known as [*operator overloading*](https://www.geeksforgeeks.org/cpp/operator-overloading-cpp/). For example, we can make use of the *addition operator (+)* for string to concatenate two *strings* and for *integer* to add two integers. The *<<* and *>> operator* are *binary shift operators* but are also used with *input and output streams*. This is possible due to operator overloading.
In C++, most operators can be overloaded to work with user-defined types.
### Key Points:

1. **Applies to user-defined types** (classes/structs).    
2. **Syntax:** Use the keyword `operator` followed by the operator symbol.
3. **Overloadable operators:** Most arithmetic (`+`, `-`, `*`, `/`), relational (`==`, `<`, `>`) and stream operators (`<<`, `>>`).
4. **Cannot change operator precedence or arity** (number of operands).

```cpp
#include <iostream>
#define e endl
using namespace std;
class Complex{
    int real,img;
    public:
    inline Complex(){}
    Complex(int real , int img){
      this->real=real;
      this->img=img;
    }
    
    Complex gibberishName(Complex &c)//here c is c2
    {
       Complex ans;//basically creating a answer object
       ans.real=real+c.real;//or ans.real=this->real+c.real;
       ans.img=img+c.img;
       return ans;
    }
    //fully same thing as above
    Complex operator +(Complex &c)//here c is c2
    {
       Complex ans;
       //this pointer points to calling object,here the calling object is c1
       ans.real=this->real+c.real;
       ans.img=this->img+c.img;
       return ans;
    }
    void display(){
      cout<<real<<" +i"<<img<<e;
    }
};

int main()
{
    Complex c1(5,6);
    Complex c2(7,8);
    Complex c3=c1.gibberishName(c2);//it is something like c1(c2)
    Complex c4=c1.operator +(c2);
    Complex c5=c1+c2; //only works if both are complex objects
    c3.display();
    c4.display();
    c5.display();
}

```

#Note:
- `this` does not point to the result (`c3`).
- `this` only points to the calling object which called the function.(`c1` here) 

### which operator can't be overloaded

1. **Scope resolution operator** `::` 
2. **Member selection operator** `.`
3. **Pointer-to-member operator** `.*`
4. **Ternary (conditional) operator** `?:`
5. **sizeof** operator
6. **typeid** operator (from RTTI)
7. **dot (.) operator for direct member access**
8. **static_cast, dynamic_cast, const_cast, reinterpret_cast**

# Runtime polymorphism

#note:  This is not runtime polymorphism, this is compile time polymorphism
### Function Hiding (It is not true function overriding)
### Function Hiding Explained

1. When a derived class declares a method with the **same name** as a method in the base class, **the base class method is hidden** in the scope of the derived class.
2. **Without `virtual`**, the compiler resolves which function to call **at compile-time**, based on the **type of the object or reference**.
3. You can still access the hidden base class method explicitly using:
     `c1.Parent::display();`
4. If i do something like 
    `Parent *p=new Child(); //child object creation during runtime` 
    `p->display()  //it will basically call the parent class's display`


```cpp
#include <iostream>
using namespace std;
class Parent{
    public:
    void display()
    {
       cout<<"here in the parent class"<<endl;
    }
};

class Child:public Parent{
    public:
    void display()
    {
       cout<<"here in the child class"<<endl;
	Parent::display();//another way to call the Parent class's method
    }
};

int main(){
  Child c1;
  c1.display();//will call the child class, because the child class will                          override the parent class's display method
  c1.Parent::display();//will explicitly call the parent class's display method
  
  Parent *p = new Child();
  p->display();//it calls the parent class's display method, not the display 
               //method of Child class and it is decided in the compile time only
 
 //the thing is that, it is alreay decided in the compile time, as soon as the 
 //pointer p is created, initially it points to parent class and the Child          object will be allocated to pointer p during runtime. So, in the compiler time is already decided and pointer p points to parent class , so it will print the parent class's display.
 
}
```




Also known as *late binding* and *dynamic polymorphism*, the function call in [*runtime polymorphism*](https://www.geeksforgeeks.org/cpp/virtual-functions-and-runtime-polymorphism-in-cpp/) is resolved at runtime in contrast with compile time polymorphism, where the compiler determines which function call to bind at compilation. Runtime polymorphism is implemented using function overriding with virtual functions.

### Function overriding 

[*Function Overriding*](https://www.geeksforgeeks.org/cpp/function-overriding-in-cpp/) occurs when a derived class defines one or more member functions of the base class. That base function is said to be *overridden*. The base class function must be declared as [*virtual function*](https://www.geeksforgeeks.org/cpp/virtual-function-cpp/) for runtime polymorphism to happen.

### Conditions:

- The base class function must be `virtual`.
- The derived class must use the same signature.
- It's a form of runtime polymorphism (dynamic binding).

The real power of **overriding** comes when you use **a base class pointer or reference pointing to a derived object**:

`Parent* p = new Child(); p->display();  // Calls Child::display() ✅`
- This is  **runtime polymorphism**
- Only works if `Parent::display()` is declared `virtual`.
- If `display()` is not virtual, this will **call the base class version**, not the derived one.






#verbose_notes

function-defined outside a class
method -defined inside a class

//method of base class  and derived class and trying to call the method of Base class from the derived class
```cpp
void display : A :: display(){}      ///wrong

//: is used to intialize only

void display{
//something
A::display() // or objB.A::display()    //right
}
```


//where A is the base class and `:` is called the `constructor initializer list`

//pure virtual function - suppose multiple methods are there in a specific class  , lets call it as A,B,C,D and if any one of it is declared as pure virtual function , then the whole class will be considered as an abstract and its object will not be created. Abstract serves as a blueprint, like structure , based on it , different objects can inherit the values;
### 🔹 Rule in C++

If a class **inherits** from a base class that has a **pure virtual function**, then:

1. **If the derived class overrides the pure virtual function:**
    
    - ✅ It becomes a concrete class.
        
    - ✅ You **can create objects** of this derived class.
        
2. **If the derived class does NOT override the pure virtual function:**
    
    - ❌ The derived class itself becomes **abstract**.
        
    - ❌ You **cannot create objects** of this derived class.
        
    - It can still be used as a **base class** for further derivation.


# Aniket is a good boy
[aniket](https://google.com)
```cpp
#inlcude <iostream>
using namespace std;
int main()
{
cout<<"hi"<<endl;
}

```



