
# IMPORTANT CONCEPTS
- _Platform independence:_ `.class` file can be run from anywhere. Suppose it is compiled in windows operating system, the `.class` file generated can be run on linux, mac or any other os.
- If  `public` class is there, the file name must be public
- if we run `javac` .class file is generated, but after version 11, java introduced a new mode call source file mode, where a java program can be compiled and run  using the command java fileName.java, and in that case the .class file won't be generated rather it will get generated in memory.The .class file is generated in a temporary way in memory and is not stored in locally
- #newVersion In compact code and instance, the main method can be written as 
    
    ```java 
         void main(String args[])
         {
            System.out.println("This new way was in preview in java version 21 to 24");
            System.out.println("It was later finallized in version 25");
         }
     ```
 #validWay :
- 1
 ```java
       void main(String args[])
       {
          System.out.println("This is also valid");
       }
 ```
- 2
```java
public class Demo{
       void main(String args[])
       {
          System.out.println("This is also valid");
       } 
 }
 ```
 

# Dynamic strings printing
```java 

public class Demo {
    public static void main(String[] args) {
        int age = 22;
        String name = "Gautam";

        System.out.println(STR."Hello my name is \{name} and my age is \{age}");
    }
}

```

# Java doc comments
- Single line 
- Multi line
- java doc comments

```java
 /**
 *This is an example of java doc comment. {@link Stable}
 */
```
