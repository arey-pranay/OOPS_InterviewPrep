# OOPS_InterviewPrep
## Extra
 - All classes extend the "Object" class.
 - Objects have "null" value by default ( including String )
 - 84.5f converts it to float or somethign, ig
 - In java, reference variables are always passed by value, and objects are always passed by reference. That's why the swap function also does not work normally.
 - The @Override is called an annotation. It  is not mandatory but you should use it to catch any errors in namiing or signatures, at compile time
 ##  Doubts
 - What is "super" and access specifiers and wrapper classes exactly ?

## Classes

Class is a blueprint or template of a real-world entity.
- It is a collection of multiple variables and functions. It's like your own new datatype.
  - e.g. the vehicle class is used to create cars bikes scooters. the car class is used by maruti, ferrari and BMW for their own custom use-cases, the last independant product is an object
- Objects are stored in heap memory, but reference variables are stored in stack memory.
- Instance variables are the variables declared inside the class and outside the method.
- We use the dot (.) operator, aka the seperator to access the instance variables. It binds the instance variable to the reference variable.
- Student s1 -> this is the declaration of a reference variable for an object in near future.

### new Keyword
- dynamically allocates memory, (i.e., on the runtime)
- Student s1 = new Student();
- only after writing this RHS, you can print the instance variables and get the default values.
- LHS is allocated on compile time, RHS is allocated on runtime.

### Constructor
- The name is same as class name. Similar to a function, but without return type (because the return type is the class).
- Default constructor has no parameters, when you put parameters it becomes a parameterized constructor. 
- It binds the values to the instance variables conviniently.
- You can also create a constructor that accepts a full object inside it.
- You can also call one constructor from another constructor.
     ```
     Student() {
        this(1,"RandomPerson..",95);
      }
     ```

### this Keyword
- It is used to access the "reference variable" ke "instance variable".
- It can be thought of like a placeholder.
- Whenever it's called "this" is replaced by the "reference variable".

### final keyword 
 - final int i = 10; it makes the variable as constant, and no changes can be made to it later.
 - But this is only true for primitive datatypes. Because for objects, it gets complicated.
  ```
   final Student s1 = new Student("Pranay");
   s1.name = "Parikh"; //valid
   s1 = new Student("Parikh); //invalid
```

### Garbage Collection
 - It is automatically handled by java, but we get the chance to do something specific whenever the object is removed and destroyed by the Grabage Collector.
 - ```
   @Override  
    protected void finalize()   
    {   
        System.out.println("finalize method called");   
    }
   ```

### Packages
 - It can be thought of as a package.
 - It helps you create compartments for the classes that you creaate and also solve the naming conflicts for different classes.
 - Outside a package, you can access only the public elements of a class.

### static keyword
 - Properties or functions that are independant of the object, are marked as static.
 - They belong to the class. It implies that you can use it without creating an object of that class.
 - Updating a static variable inside a function is achieved by classname.variable instead of this.variable
 - Inside a static method, you can only use static variables and methods.
 - It is like, if you want to be executed, either make yourself static, or get an object to execute you.
 - And since main function is static always, it's easier to create independant functions as static.
 - Also, static functions don't have objects, you cannot use "this" keyword in static contexts.
 - All static stuff is executed at compile-time because it has nothing to do with the classes' objects.

### static block
```
public class Solution {
    static int a = 4;
    static int b;

    // will only run once, when the first obj is create i.e. when the class is loaded for the first time
   // so only when the first object is created, then this static block will be ran, from second object onwards, this will be like non-existent
    static {
        System.out.println("I am in static block");
        b = a * 5;
    }
}
```

### Singleton Classes
- Classes of which only 1 object can be created.
- So you are not publicly allowed to use the constructor. Use a public method to call that constructor and return the same object everytime from that function.
- You can privately maintain an instance of your class and privately call the constructor depending on if that instance already exists.
```
public class ST {
    //private constructor
    private ST () {

    }
    //private static object
    private static ST instance;
    //public function to call from different classes.
    public static ST getInstance() {
        // check whether 1 obj only is created or not
        if (instance == null) {
            instance = new ST();
        }
        return instance;
    }
}
```

## Pillars of OOPS

### Inheritence
- There is a Base Class (Parent Class), and the Class derived from it is called Child Class
-  ```
   Class Child extends Base{

   }
   ```
- The property is first looked into the Child Class and then the Parent Class.
- Children cannot access private members of Parent Class.
- Parent class object cannot Child class.
  
- ###### Super Keyword
  
   -  1.  It is used to call the constructor of the parent class from the child class.
   - ```
     public 2D{
        int x;
        int y;
        2D(int a, int b){
           this.x = a;
           this.y = b;
         }
     }
     public 3D extends 2D{
        int z;
        3D(int a, int b, int c){
           super(a,b); //always initialize supercalss before child class
           this.z = c;
         }
     }
   ```
   
   - 2. It is used when parent and child have a common named var, but you want to access the parent class var or function
   Let's say both 2D and 3D have a material variable, then from 3D (Child) if you want to access the 2D's (Parent's) material, then you do the following:
   System.out.println(super.material);
- ##### Trying something weird (Upcasting)
   - Parent p = new Child(); //valid
   - It is the type of the reference variable and not the type of the object, that determines what members can or cannot be accessed.
   - So 'p' cannot access the properties of Child class.
   - But Parent Classes don't always know all Child classes, therefore Child reference variable cannot be used to initialize parent object, because parent constructor will not have everything needed for a child reference variable.
   -  Child c = new Parent(); //invalid
   -  In a parent class constructor that takes a parent object, you can also pass a child object, because everything that the parent needs, the child will have.
   -  But the opposite is not true, you cannot give a parent object to a child constructor, because a child wants more than that.
 - #### Types of Inheritence
    - Single Inheritence
    - Multi-level Inheritence
    - Multiple Inheritence (Multiple Parents for 1 Child) (Not Allowed in Java) (We use Interfaces for this purpose)
    - Heirarchical Inherience (1 Parent has Multiple Children)

 ### Polymorphism
  - Multiple Ways to represent the same thing
  - e.g. creating a shape class with a default function for area, and then having multiple types of shapes as its children, each having their own area function.
  - The function called is dependant on the type of object and not type of reference variable.
  - Types of Polymorphism
     - Compile Time (Static) (By Overloading) Same Name but either different arg type, return type, order of args, or different no. of args
     - Runtime (Dynamic) (By Overriding), When everything is same. @Override annotations can be used.
   - When you say Shapes s = new Circle(); and then s.area(), then Shapes must have a function called "area()" and then while executing, firstly the area() method will be checked under Circle, because the object type is circle.
   - So the existence or Static stuff depends on LHS or the reference variable. (At compile Time)
   - And the decision of what to execute or Dynamic stuff depends on RHS or the object type. (At runtime)
   - So LHS decides what can be accessed, RHS decides what exactly will be accessed.
   - This is called Dynamic Method Dispatch or "Late Binding".
   - But if you put "final" in front of a method, then it cannot be overriden, and it is then called "Early Binding"
   - Similarly static methods also cannot be overriden.
   - The instance variables also are never overloaded or overriden.
