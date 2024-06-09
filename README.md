# OOPS_InterviewPrep
## Extra
 - Objects have "null" value by default ( including String )
 - 84.5f converts it to float or somethign, ig
 - In java, reference variables are always passed by value, and objects are always passed by reference. That's why the swap function also does not work normally.
 ##  Doubts
 - What is "super" and "@Override" and access specifiers and wrapper classes exactly ?
## Classes

Class is a blueprint or template of a real-world entity.
- It is a collection of multiple variables and functions. It's like your own new datatype.
  - e.g. the vehicle class is used to create cars bikes scooters. the car class is used by maruti, ferrari and BMW for their own custom use-cases, the last independant product is an object
- Objects are stored in heap memory, but reference variables are stored in stack memory.
- Instance variables are the variables declared inside the class and outside the method.
- We use the dot (.) operator, aka the seperator to access the instance variables.
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
     ``` Student() {
        this(1,"RandomPerson..",95);
      } ```

### this Keyword
- It is used to access the "reference variable" ke "instance variable".
- It can be thought of like a placeholder.
- Whenever it's called "this" is replaced by the "reference variable".

### final keyword 
 - final int i = 10; it makes the variable as constant, and no changes can be made to it later.
 - But this is only true for primitive datatypes. Because for objects, it gets complicated.
 - ```final Student s1 = new Student("Pranay");
   s1.name = "Parikh"; //valid
   s1 = new Student("Parikh); //invalid ```

### Garbage Collection
 - It is automatically handled by java, but we get the chance to do something specific whenever the object is removed and destroyed by the Grabage Collector.
 - ```   @Override  
    protected void finalize()   
    {   
        System.out.println("finalize method called");   
    }   ```
   
