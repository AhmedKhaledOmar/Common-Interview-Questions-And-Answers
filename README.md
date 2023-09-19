# Common-Interview-Questions-And-Answers (All Examples using C# language)
## **General Topics:**
-----------------------------------------------------------------------------------
### Q- What is Casting and what are the types of casting in C#? (With)
Casting is the process of converting a value from one data type to another in C#. There are several types of casting that you can use to convert values:

Implicit Casting: This is when the compiler automatically converts a value from one type to another, if it can be done safely. For example, you can implicitly cast an int to a double, because there is no loss of precision.

Explicit Casting: This is when you explicitly tell the compiler to convert a value from one type to another. Explicit casting requires the use of a cast operator, which is a set of parentheses containing the target type. For example, you can explicitly cast a double to an int by using the cast operator, like this: (int)3.14.

Boxing: This is the process of converting a value type to a reference type, by wrapping the value type in an object. For example, you can box an int by assigning it to an object, like this: object obj = 42;.

Unboxing: This is the process of extracting the value from a boxed object and converting it back to a value type. For example, you can unbox an int by casting the object to an int, like this: int i = (int)obj;.

Here's an example of casting in C#:

<pre>
// Implicit Casting
int x = 5;
double y = x; // No cast operator required

// Explicit Casting
double a = 3.14;
int b = (int)a; // Cast operator required

// Boxing
int c = 42;
object obj = c; // Boxing c into an object

// Unboxing
int d = (int)obj; // Casting obj back to an int
</pre>
In the above example, we use implicit casting to convert an int to a double, and explicit casting to convert a double to an int. We also demonstrate boxing by assigning an int to an object, and unboxing by casting the object back to an int.

Casting is a powerful tool in C#, but it should be used with care, as it can lead to unexpected results if not used properly. It is important to understand the limitations of each type of casting, and to be mindful of potential data loss or type mismatches when converting values.

-----------------------------------------------------------------------------------
### Q- What will happen in each case? (C#) (With)
### object obj = null;
### - int d = (int)obj;
### - int d = obj as int ;
### - int d = Int64.Parse(obj);
### - int d = Int64.TryParse(obj)
### - int d = obj is int ;

In the following code, obj is declared as a null object reference of type object:

<pre>
object obj = null;
Now, let's take a look at what happens in each of the scenarios you provided:

int d = (int)obj;: This is an explicit cast that attempts to convert the null reference obj to an int. This will result in a System.NullReferenceException at runtime, because you cannot cast a null reference to a value type like int.

int d = obj as int;: This is a safe cast that attempts to convert obj to an int, but instead of throwing an exception if the cast fails, it returns null. Since obj is a null reference, the result of this cast will also be null. The resulting value of d will be 0 (the default value for int), because the variable was not assigned any other value.

int d = Int64.Parse(obj);: This is an attempt to parse the null reference obj as a long value using the Int64.Parse method. This will result in a System.ArgumentNullException at runtime, because Int64.Parse does not accept null arguments.

int d = Int64.TryParse(obj, out long result);: This is an attempt to parse the null reference obj as a long value using the Int64.TryParse method. This method is a safe way to convert a string to a long value, because it returns true if the parse succeeded and false if it failed. Since obj is a null reference, the parse will fail and the value of d will be 0 (the default value for int), because the out parameter result will not be assigned any other value.

int d = obj is int;: This is a type check that returns false, because obj is not an instance of int. The resulting value of d will be false, which is a bool value.
</pre>
In general, it's important to be careful when casting, parsing or checking the type of null references, because these operations can throw exceptions or return unexpected results. It's a good practice to check if an object is null before attempting to cast, parse or use it, to avoid null reference exceptions.

-----------------------------------------------------------------------------------
### Q - What are Ref and out Keywords in C# ? (With)
In C#, ref and out are keywords that are used to pass arguments by reference in a method call. Here's what each of them does:

ref keyword: The ref keyword is used to pass a parameter by reference to a method. This means that any changes made to the parameter inside the method will be reflected outside the method as well. The variable passed with ref must be initialized before it is passed.
Here's an example:

<pre>
public void Increment(ref int x)
{
    x++;
}

int num = 5;
Increment(ref num);
// num will now be 6
</pre>
In this example, the Increment method takes an int parameter x by reference using the ref keyword. When we pass the variable num to this method with ref, any changes made to x inside the method will be reflected in the num variable outside the method.

out keyword: The out keyword is similar to ref, but it is used for returning values from a method rather than passing them as input. The out parameter does not need to be initialized before it is passed.
Here's an example:
<pre>
public void Divide(int x, int y, out int quotient, out int remainder)
{
    quotient = x / y;
    remainder = x % y;
}

int num1 = 10;
int num2 = 3;
int result, remainder;
Divide(num1, num2, out result, out remainder);
// result will be 3 and remainder will be 1
</pre>
In this example, the Divide method takes two integer parameters x and y and uses the out keyword to return two integer values quotient and remainder. When we call this method, we pass the result and remainder variables with the out keyword. After the method call, these variables will contain the values of quotient and remainder, respectively.

Note that when using out, the method must assign a value to the output parameter before the method returns, otherwise the code will not compile.

-----------------------------------------------------------------------------------
</br>

## **OOP:**
### Q- What is OOP? (With)

OOP stands for Object-Oriented Programming. It is a programming paradigm or style of programming that is based on the concept of "objects" which can contain data and code to manipulate that data.

In OOP, a program is designed by creating classes, which are like blueprints or templates for creating objects. Each class defines a set of attributes (also known as properties or data members) and methods (functions or procedures) that can be used to manipulate those attributes.

An object is an instance of a class, and it contains specific data values for each of its attributes. The methods defined in the class can be used to manipulate the data within the object.

OOP provides several benefits, including code reusability, encapsulation, and the ability to model real-world objects and concepts more accurately. It is widely used in software development, and many popular programming languages, such as Java, Python, and C++, support OOP principles.

**ْNote** : In short anything in my project I treat it as an object

-----------------------------------------------------------------------------------
###  Q- What are OOP Types ? (With)
In C#, there are four main types of OOP. These are:

1-Abstraction
2-Encapsulation
3-Inheritance
4-Polymorphism
Here's a brief explanation of each:

Abstraction: Abstraction is the process of hiding unnecessary details while exposing only the essential features of an object. It is achieved through the use of abstract classes and interfaces. An abstract class is a class that cannot be instantiated but can be used as a base class for other classes. An interface is a contract that specifies a set of methods and properties that a class must implement. Abstraction helps to reduce complexity and increase maintainability of the code.

Encapsulation: Encapsulation is the practice of wrapping data and methods into a single unit (i.e. class) and restricting access to the data from outside the class. It helps to achieve data integrity and security by preventing unauthorized access or modification of the data. Encapsulation in C# is achieved through the use of access modifiers such as public, private, protected, and internal.

Inheritance: Inheritance is the process of creating new classes that are derived from existing classes. The new class, called the derived class, inherits all the properties and methods of the existing class, called the base class. This enables code reuse and promotes code efficiency. In C#, inheritance is achieved using the "class : baseclass" syntax.

Polymorphism: Polymorphism is the ability of an object to take on many forms. In C#, there are two types of polymorphism: compile-time polymorphism and run-time polymorphism. Compile-time polymorphism is achieved through method overloading, while run-time polymorphism is achieved through method overriding.

Method overloading allows multiple methods to have the same name, but with different parameters. This helps to avoid naming conflicts and improves code readability. Method overriding, on the other hand, enables a derived class to provide its own implementation of a method that is already defined in its base class.

In conclusion, these four types of OOP principles are crucial in designing efficient and maintainable software systems in C#. Abstraction, encapsulation, inheritance, and polymorphism help to achieve code reusability, code efficiency, and maintainability.

-----------------------------------------------------------------------------------
### Q - Difference between Abstraction and Encapsulation? (With)
Abstraction and Encapsulation are two important concepts in Object-Oriented Programming (OOP) that are often confused with each other, but they are different in terms of their meaning and implementation.

Abstraction is the process of hiding unnecessary details while exposing only the essential features of an object. It is achieved by defining abstract classes and interfaces that define the contract for the behavior of the object, without specifying how the behavior is implemented. Abstraction provides a way to represent complex systems in a simplified manner, allowing developers to focus on the most important aspects of the system. It helps to reduce complexity and increase maintainability of the code.

On the other hand, Encapsulation is the practice of wrapping data and methods into a single unit (i.e. class) and restricting access to the data from outside the class. It helps to achieve data integrity and security by preventing unauthorized access or modification of the data. Encapsulation ensures that the implementation details of a class are hidden from other objects, providing a clear separation between the interface and the implementation.

In summary, the key difference between Abstraction and Encapsulation is that Abstraction focuses on hiding unnecessary details and providing a simplified view of the object, while Encapsulation focuses on hiding the implementation details and providing a clear separation between the interface and the implementation. Both Abstraction and Encapsulation are important principles in OOP that help to achieve code reusability, code efficiency, and maintainability.

-----------------------------------------------------------------------------------
### Q - What's dynamic polymarphism? (With)
Dynamic Polymorphism, also known as runtime polymorphism or late binding, is a concept in Object-Oriented Programming (OOP) that allows an object to take on many forms at runtime. It is achieved through method overriding, which enables a derived class to provide its own implementation of a method that is already defined in its base class.

In dynamic polymorphism, the specific implementation of a method to be called is determined at runtime based on the actual type of the object, rather than its declared type. This means that a method call on an object of a derived class can result in different behavior than the same method call on an object of its base class.

Dynamic polymorphism is a powerful feature in OOP that allows developers to create code that is more flexible, reusable, and extensible. It enables the creation of a generic code that can work with multiple objects, without knowing their specific types. Dynamic polymorphism is particularly useful in situations where the exact type of an object is not known at compile time, but is determined at runtime.

In C#, dynamic polymorphism is achieved through the use of the virtual and override keywords. The base class declares a method as virtual, and the derived class overrides the method by providing its own implementation. When a method call is made on an object of the derived class, the overridden method is called instead of the virtual method defined in the base class

-----------------------------------------------------------------------------------
### Q - Difference between method overloading and overriding? (With)
n C#, both method overloading and method overriding are used to achieve polymorphism, but they are different concepts.

Method overloading is a feature that allows you to define multiple methods with the same name but with different parameters. Overloading a method means defining a method with the same name as an existing method but with a different signature. The method signature includes the method name, parameter types, and the number of parameters. Overloading allows you to create methods that perform similar tasks, but with different input parameters. The method that is called at runtime is determined based on the number, types, and order of the arguments passed to the method.

Here's an example of method overloading in C#:

<pre>
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b) //return type dosn't effect in this proccess
    {
        return a + b;
    }
}
</pre>
In this example, the Calculator class has two Add methods, one that takes two int parameters, and the other that takes two double parameters. The methods have the same name but different parameter types, and the appropriate method is called based on the argument types passed to the method.

Method overriding, on the other hand, is a feature that allows you to provide a new implementation for a method that is already defined in a base class or an interface. Overriding a method means providing a new implementation of a method with the same signature as the original method. The method in the derived class must have the same name, return type, and parameters as the base class method.

Here's an example of method overriding in C#:

<pre>
public class Shape
{
    public virtual double CalculateArea()
    {
        return 0;
    }
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea() //return type dosn't effect in this proccess
    {
        return Math.PI * Radius * Radius;
    }
}
</pre>
In this example, the Shape class has a virtual CalculateArea method, which returns 0. The Circle class overrides the CalculateArea method and provides its own implementation to calculate the area of a circle. The override keyword is used to indicate that the CalculateArea method in the Circle class is overriding the CalculateArea method in the Shape class.

To avoid errors during compilation, the compiler checks that the method being overridden has the same signature as the overriding method. This means that the method name, return type, and parameter types must match. If the signature does not match, the compiler will generate an error.

In summary, method overloading is used to create multiple methods with the same name but different parameter types, while method overriding is used to provide a new implementation for a method that is already defined in a base class or an interface. Both concepts are used to achieve polymorphism in C#.

-----------------------------------------------------------------------------------
### Q - What are Access Modifers?  (With)
Access modifiers in C# are keywords that determine the visibility and accessibility of classes, properties, methods, and other members in a program. In C#, there are five access modifiers:

public: Public members are accessible from any part of the program. A public member can be accessed from the same assembly or from a different assembly.
Example:

<pre>
public class Employee
{
    public string Name { get; set; }
    public int Age { get; set; }
}
</pre>
In this example, the Name and Age properties are declared as public, which means they can be accessed from anywhere in the program.

private: Private members are accessible only within the same class. Private members are not visible from outside the class.
Example:

<pre>
public class Employee
{
    private int salary;

    public void SetSalary(int amount)
    {
        salary = amount;
    }
}
</pre>
In this example, the salary field is declared as private, which means it can be accessed only from within the Employee class.

protected: Protected members are accessible within the same class and any derived classes. Protected members are not visible from outside the class hierarchy.
Example:

<pre>
public class Shape
{
    protected double area;

    protected virtual void CalculateArea()
    {
        // Calculate area of the shape
    }
}

public class Circle : Shape
{
    public void DisplayArea()
    {
        CalculateArea();
        Console.WriteLine($"Area: {area}");
    }

    protected override void CalculateArea()
    {
        // Calculate area of the circle
        area = Math.PI * Radius * Radius;
    }

    public double Radius { get; set; }
}
</pre>
In this example, the Shape class has a protected area field and a protected virtual CalculateArea method. The Circle class inherits from the Shape class and overrides the CalculateArea method to calculate the area of a circle. The area field is accessible from within the Circle class, but not from outside the class hierarchy.

internal: Internal members are accessible only within the same assembly. An assembly is a collection of one or more modules that are built as a unit.
Example:

<pre>
internal class Calculator // Can read any class in any class has same namespace
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
</pre>
In this example, the Calculator class is declared as internal, which means it can be accessed only from within the same assembly.

protected internal: Protected internal members are accessible within the same assembly and any derived classes.
Example:

<pre>
public class Shape
{
    protected internal double area;

    protected internal virtual void CalculateArea()
    {
        // Calculate area of the shape
    }
}

public class Circle : Shape
{
    public void DisplayArea()
    {
        CalculateArea();
        Console.WriteLine($"Area: {area}");
    }

    protected internal override void CalculateArea()
    {
        // Calculate area of the circle
        area = Math.PI * Radius * Radius;
    }

    public double Radius { get; set; }
}
</pre>
In this example, the Shape class has a protected internal area field and a protected internal virtual CalculateArea method. The Circle class inherits from the Shape class and overrides the CalculateArea method to calculate the area of a circle. The area field is accessible from within the Circle class and any other class within the same assembly, but not from outside the assembly.

-----------------------------------------------------------------------------------
### Q - What are Non-Access Modifers?  (With)
Non-access modifiers are keywords in C# that modify the behavior of classes, methods, and other members in a program, but do not affect their accessibility or visibility. In C#, there are four non-access modifiers:

static: The static modifier is used to create a single instance of a member that can be accessed without creating an instance of the class. Static members belong to the class itself, not to any particular instance of the class.
Example:

<pre>
public class MathUtils
{
    public static int Add(int a, int b)
    {
        return a + b;
    }
}
</pre>
In this example, the Add method is declared as static, which means it can be accessed without creating an instance of the MathUtils class.

abstract: The abstract modifier is used to define an abstract class or an abstract method. An abstract class cannot be instantiated directly and can only be used as a base class for other classes. An abstract method does not have an implementation and must be overridden in a derived class.
Example:

<pre>
public abstract class Shape
{
    public abstract double Area { get; }

    public abstract void Display();
}
</pre>
In this example, the Shape class is declared as abstract, which means it cannot be instantiated directly. The Area and Display methods are declared as abstract, which means they do not have an implementation and must be overridden in any derived class.

sealed: The sealed modifier is used to prevent a class from being inherited by other classes. Sealed classes cannot be used as a base class for other classes.
Example:
<pre>
public sealed class Circle
{
    public double Radius { get; set; }

    public double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}
</pre>
In this example, the Circle class is declared as sealed, which means it cannot be inherited by any other class.

virtual: The virtual modifier is used to allow a method to be overridden in a derived class. A virtual method has an implementation in the base class, but can be overridden in a derived class.
Example:
<pre>
public class Shape
{
    public virtual void Draw()
    {
        // Draw the shape
    }
}

public class Circle : Shape
{
    public override void Draw()
    {
        // Draw a circle
    }
}

public class Rectangle : Shape
{
    public override void Draw()
    {
        // Draw a rectangle
    }
}
</pre>
In this example, the Shape class has a virtual Draw method, which has an implementation in the base class. The Circle and Rectangle classes override the Draw method to provide their own implementations.

-----------------------------------------------------------------------------------
### Q - What is the usage of new keyword with a method in a class ? (With)
In C#, the new keyword is used to declare a member in a derived class that has the same name as a member in the base class. This is called "hiding" the base class member, and it allows the derived class to have its own implementation of the member that is independent of the base class.

Here's an example:

<pre>
public class Animal
{
    public void Eat()
    {
        Console.WriteLine("The animal is eating.");
    }
}

public class Cat : Animal
{
    public new void Eat()
    {
        Console.WriteLine("The cat is eating.");
    }
}
</pre>
In this example, the Animal class has an Eat method that writes a message to the console. The Cat class also has an Eat method that writes a message to the console, but it is declared with the new keyword to hide the base class Eat method.

Now, if we create an instance of the Cat class and call the Eat method, we'll see the message from the Cat class:
<pre>
Cat myCat = new Cat();
myCat.Eat(); // Output: The cat is eating.
//If we cast the Cat instance to an Animal instance and call the Eat method, we'll see the message from the Animal class, 
//because the new keyword only affects the member in the derived class, not the base class:
Animal myAnimal = (Animal)myCat;
myAnimal.Eat(); // Output: The animal is eating.
</pre>

-----------------------------------------------------------------------------------
### Q -  Difference between access and non-access modifiers ? (With)
In C#, access modifiers are used to control the accessibility or visibility of classes, methods, fields, properties, and other members in a program, while non-access modifiers modify the behavior of these members without affecting their accessibility.

Access modifiers determine who can access a member and from where, while non-access modifiers determine how a member behaves and what it can do.

Here are some differences between access and non-access modifiers:

Accessibility: Access modifiers control the accessibility of a member, while non-access modifiers do not.

Visibility: Access modifiers control where a member can be accessed from (e.g. within the same class, within the same assembly, or from any assembly), while non-access modifiers do not affect visibility.

Inheritance: Access modifiers can affect the inheritance of a member, such as when a member is marked as private and cannot be accessed by derived classes. Non-access modifiers do not affect inheritance.

Behavior: Non-access modifiers modify the behavior of a member, such as when a method is marked as static and can be called without an instance of the class. Access modifiers do not modify behavior.

Examples of access modifiers include public, private, protected, and internal. Examples of non-access modifiers include static, virtual, abstract, and sealed.

In general, access modifiers are used to control who can access a member, while non-access modifiers are used to modify the behavior of a member. Together, access and non-access modifiers allow developers to control the accessibility and behavior of members in a program, making it easier to create robust and maintainable software.

-----------------------------------------------------------------------------------
### Q -  When a child class inherits from a parent class and overrides a method, Which method will be invoked if we call the overridden method from child class? (With)
When a child class inherits from a parent class and overrides a method, the method that is called depends on the type of the object that the method is called on. If the object is an instance of the child class, the overridden method in the child class is called. If the object is an instance of the parent class, the method in the parent class is called.

Here's an example:
<pre>
public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("The animal makes a sound.");
    }
}

public class Cat : Animal
{
    public override void Speak()
    {
        Console.WriteLine("The cat meows.");
    }
}
</pre>
In this example, the Animal class has a Speak method that writes a message to the console. The Cat class overrides the Speak method with its own implementation.

Now, if we create an instance of the Cat class and call the Speak method, we'll see the message from the Cat class:
<pre>
Cat myCat = new Cat();
myCat.Speak(); // Output: The cat meows.
If we cast the Cat instance to an Animal instance and call the Speak method, we'll still see the message from the Cat class, because the override keyword overrides the base class method and replaces it with the derived class method:
</pre>
<pre>
Animal myAnimal = (Animal)myCat;
myAnimal.Speak(); // Output: The cat meows.
</pre>
However, if we create an instance of the Animal class and call the Speak method, we'll see the message from the Animal class, because the override keyword only affects the method in the derived class, not the base class:

<pre>
Animal myAnimal = new Animal();
myAnimal.Speak(); // Output: The animal makes a sound.
</pre>

-----------------------------------------------------------------------------------
### Q -  Difference between singelton and static class?
Singleton and static classes are two different design patterns in C# that are used to create classes that have only one instance in memory. However, they have some differences in implementation and behavior.

A singleton class is a class that can only have one instance in memory at any given time. It is created using a private constructor and a static method to retrieve the single instance. Singleton classes are often used for classes that manage system resources or have global state.

Here's an example of a singleton class:
<pre>
public class MySingleton
{
    private static MySingleton _instance;

    private MySingleton()
    {
        // Constructor is private so that instances cannot be created outside the class
    }

    public static MySingleton GetInstance()
    {
        if (_instance == null)
        {
            _instance = new MySingleton();
        }
        return _instance;
    }
}
</pre>
In this example, the MySingleton class has a private constructor, which prevents instances of the class from being created outside the class. The GetInstance method is a static method that returns the single instance of the class, creating it if necessary.

On the other hand, a static class is a class that cannot be instantiated and can only contain static members, such as methods and fields. Static classes are often used for utility classes that provide common functionality to other classes.

Here's an example of a static class:
<pre>
public static class MyStaticClass
{
    public static void MyStaticMethod()
    {
        // Static method implementation
    }
}
</pre>
In this example, the MyStaticClass class is marked as static, which means it cannot be instantiated. It contains a single static method that can be called from other classes without creating an instance of the class.

So, the main differences between a singleton class and a static class are:

A singleton class can be instantiated and can have state, while a static class cannot be instantiated and cannot have state.
A singleton class is used to control the creation and access to a single instance of a class, while a static class is used to provide utility methods and constants.
It's important to choose the right design pattern based on the needs of your application, as both singleton and static classes have their own benefits and drawbacks.

-----------------------------------------------------------------------------------
### Q -  Difference between interface and abstract class? and what's new in C# about interfaces ? (With)
In C#, interfaces and abstract classes are two different ways to define a contract for derived classes to implement. They have some similarities, but also some important differences.

An interface is a type that defines a set of public methods, properties, events, and indexers that a class must implement. An interface does not provide any implementation details, only the definition of the members that a class must implement. An interface can be used to define a common contract for multiple classes, even if those classes have different base classes.

Here's an example of an interface:
<pre>
public interface IShape
{
    double CalculateArea();
    double CalculatePerimeter();
}
</pre>
In this example, the IShape interface defines two methods that a class must implement to be considered a shape. Any class that implements this interface must provide its own implementation for these methods.

An abstract class, on the other hand, is a class that cannot be instantiated and can contain both abstract and non-abstract members. An abstract class provides a partial implementation of a class, leaving some of the implementation details to derived classes. An abstract class can be used to define a common base for multiple classes, and can contain state and behavior that is shared by all derived classes.

Here's an example of an abstract class:
<pre>
public abstract class Shape
{
    public abstract double CalculateArea();
    public abstract double CalculatePerimeter();

    public virtual void Draw()
    {
        // Default implementation of Draw method
    }
}
</pre>
In this example, the Shape class is marked as abstract, which means it cannot be instantiated. It defines two abstract methods that must be implemented by any derived classes, but also provides a default implementation of a Draw method. Derived classes can override the Draw method if they need to provide their own implementation.

As for what's new in C# about interfaces and abstract classes, in C# 8.0 and later, interfaces can now contain default implementations for methods, which means that you can provide a default implementation for an interface method without forcing all implementing classes to provide their own implementation. Additionally, in C# 9.0 and later, abstract classes can now have implementation for interface members, which means that an abstract class can provide a default implementation for an interface method that derived classes can choose to override or not.

### More on this comparison :  

Both abstract classes and interfaces are used to define abstract types in object-oriented programming. Here are some of the main differences between them:

Implementation: An abstract class can contain some implementation code, while an interface cannot. Abstract classes can provide default implementations for some or all of their methods, which can be overridden by subclasses. Interfaces, on the other hand, do not contain any implementation code at all.

Multiple inheritance: A class can only inherit from one abstract class, but it can implement multiple interfaces. This is because an abstract class is a type of class, while an interface is a separate construct that can be implemented by any class.

Accessibility: Methods and fields of an interface are by default public, while an abstract class can have different access modifiers for its methods and fields.

Purpose: Abstract classes are used to define a base class for a group of related classes, while interfaces are used to define a contract that a class must follow.

Constructors: An abstract class can have a constructor, while an interface cannot.

In general, abstract classes are used when you want to create a common base class for a group of related classes, and when you want to provide some default implementation code for those classes. Interfaces, on the other hand, are used when you want to define a contract that a class must follow, but you don't care about its implementation.

It's also worth noting that in some programming languages, such as C#, interfaces can contain default implementations for their methods using default interface methods. This blurs the distinction between interfaces and abstract classes somewhat, but the basic differences outlined above still hold.

**Note** : In last version in C# Interfaces can contain some implementation.

-----------------------------------------------------------------------------------
### Q - Abstract method and when can I not implement an abstract method in a child class ? with c# example?(With)
An abstract method is a method that does not have an implementation in the base class, and must be implemented in a derived class. To declare an abstract method in C#, you use the abstract keyword before the method signature, like this:

<pre>
public abstract void DoSomething();
Any class that has an abstract method must be declared as an abstract class using the abstract keyword:

public abstract class MyClass
{
    public abstract void DoSomething();
}
</pre>
In this example, MyClass is an abstract class with an abstract method DoSomething(). Any derived class that inherits from MyClass must implement the DoSomething() method, or else it must also be declared as an abstract class.

If you have an abstract class with abstract methods, you can choose to implement some of the methods and leave others as abstract. In this case, any non-abstract methods can provide a default implementation that derived classes can override, while any abstract methods must be implemented by derived classes. Here's an example:
<pre>
public abstract class MyBaseClass
{
    public void DoSomething()
    {
        Console.WriteLine("Doing something in base class");
    }

    public abstract void DoSomethingElse();
}

public class MyDerivedClass : MyBaseClass
{
    public override void DoSomethingElse()
    {
        Console.WriteLine("Doing something else in derived class");
    }
}
</pre>
In this example, MyBaseClass is an abstract class with a non-abstract method DoSomething() and an abstract method DoSomethingElse(). MyDerivedClass is a derived class that inherits from MyBaseClass, and it provides an implementation for the DoSomethingElse() method while inheriting the implementation of the DoSomething() method from the base class.

Note that if you have an abstract method that is not implemented in a derived class, then the derived class must also be declared as an abstract class. If you try to create an instance of a derived class that does not implement all the abstract methods of its base class, you will get a compilation error.

-----------------------------------------------------------------------------------
### Q - Difference between class and struct ? 
In C#, a class and a struct are two different types of user-defined data structures, each with its own characteristics and uses.

Here are some of the main differences between a class and a struct in C#:

Class is a reference type, whereas struct is a value type. This means that when you create an instance of a class, it is stored in memory and you get a reference to that memory location. When you create an instance of a struct, it is stored on the stack or as part of another object.

Classes support inheritance and polymorphism, while structs do not. This means that you can create a new class that extends or modifies the behavior of an existing class, but you can't do this with structs.

Classes have a default constructor, while structs do not. This means that when you create a new instance of a class, the constructor is called automatically, but you must explicitly call the constructor for a struct.

Classes have nullable types, while structs do not. This means that you can set a reference to a null value, but you can't do this with a value type.

Classes are typically used for larger and more complex data structures that require more memory and processing power, while structs are used for smaller and simpler data structures that require less memory and processing power.

Here's an example of a class in C#:

<pre>
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
    public void SayHello()
    {
        Console.WriteLine("Hello, my name is " + Name + " and I am " + Age + " years old.");
    }
}
</pre>
And here's an example of a struct in C#:
<pre>
public struct Point
{
    public int X;
    public int Y;
    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }
}
</pre>
In this example, Point is a simple struct with two fields X and Y, and a constructor that takes two arguments to set the values of these fields. Because Point is a value type, when you create a new instance of it, the values of X and Y are stored directly in memory as part of the struct.



-----------------------------------------------------------------------------------
### Q - what's Reflection ?
Reflection in C# refers to the ability of a program to examine and analyze its own metadata at runtime. It allows a program to retrieve information about types, methods, properties, and events of an object at runtime.

Here's an example to illustrate how Reflection can be used in C#:

Suppose we have a class Person as follows:

<pre>
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void PrintDetails()
    {
        Console.WriteLine($"Name: {Name}, Age: {Age}");
    }
}
</pre>
We can use Reflection to inspect this class and retrieve information about its properties and methods at runtime. Here's an example of how to do that:
<pre>
using System;
using System.Reflection;

class Program
{
    static void Main()
    {
        Type type = typeof(Person); // get the type of the Person class

        Console.WriteLine("Properties:");
        foreach (PropertyInfo property in type.GetProperties())
        {
            Console.WriteLine(property.Name);
        }

        Console.WriteLine("\nMethods:");
        foreach (MethodInfo method in type.GetMethods())
        {
            Console.WriteLine(method.Name);
        }
    }
}
</pre>
In this example, we use the typeof operator to get the Type object that represents the Person class. We then use this Type object to retrieve information about the class properties and methods using the GetProperties and GetMethods methods. We can then loop through the resulting collections of PropertyInfo and MethodInfo objects and print their names to the console.

This is just a simple example, but Reflection can be used for many other purposes, such as creating objects dynamically, invoking methods dynamically, and more. However, it should be used with caution, as it can have a negative impact on performance and can make code harder to maintain.

-----------------------------------------------------------------------------------
### Q - What's a Constructor? And What are the types of Constructor?  (With)
In C#, a constructor is a special method that is called when an object of a class is created. It is used to initialize the object's state by assigning values to its properties and performing any other required setup. The constructor has the same name as the class and does not have a return type.

There are several types of constructors in C#, including:

Default constructor: This is a parameterless constructor that is automatically generated by the compiler if no other constructor is defined. It simply initializes the object with default values for its properties.
<pre>
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    // Default constructor
    public Person()
    {
        Name = "Unknown";
        Age = 0;
    }
}
</pre>
Parameterized constructor: This is a constructor that takes one or more parameters and is used to initialize the object with specific values for its properties.
<pre>
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    // Parameterized constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
</pre>
Static constructor: This is a constructor that is called only once, when the class is first accessed. It is used to perform any one-time initialization that is required for the class.
<pre>
public class MyClass
{
    static MyClass()
    {
        Console.WriteLine("Static constructor called");
    }
}
</pre>
Private constructor: This is a constructor that is marked as private and is used to prevent the creation of objects of the class by other classes. It is typically used in conjunction with a static factory method to control the creation of objects.
<pre>
public class Singleton
{
    private static Singleton _instance;

    private Singleton()
    {
        // Private constructor
    }

    public static Singleton GetInstance()
    {
        if (_instance == null)
        {
            _instance = new Singleton();
        }

        return _instance;
    }
}
</pre>
These are just a few examples of the types of constructors that are available in C#. Constructors are a fundamental part of object-oriented programming, and they are used extensively in building classes and objects.

-----------------------------------------------------------------------------------
### Q - What's a Destructor? 
In C#, a destructor is a special method that is called automatically when an object is about to be destroyed. It is used to perform any cleanup or finalization that is required before the object is removed from memory.

A destructor is declared in a class using the tilde (~) symbol followed by the class name. It is called automatically by the garbage collector when the object is no longer referenced by any other part of the program. Unlike a constructor, a destructor cannot be called directly.

Here is an example of a destructor:
<pre>
public class MyClass
{
    public MyClass()
    {
        Console.WriteLine("Constructor called");
    }

    ~MyClass()
    {
        Console.WriteLine("Destructor called");
    }
}
</pre>
In this example, the constructor is called when an object of the class is created, and the destructor is called automatically when the object is about to be destroyed.

It's important to note that the use of destructors in C# is generally discouraged, as they can introduce unnecessary complexity and make it harder to manage memory and resources. Instead, it is generally recommended to use the IDisposable interface and the Dispose() method to perform cleanup and finalization.

-----------------------------------------------------------------------------------
### Q -What's the difference between destructor and finalize method and finally block?
In C#, a destructor, finalize method, and finally block are three different constructs that serve different purposes. Here is a brief explanation of each of them:

Destructor:
A destructor is a method that is automatically called by the Garbage Collector (GC) when an object is about to be destroyed. The purpose of the destructor is to release any unmanaged resources that the object may be holding. Unlike in C++, destructors in C# are not used to deallocate memory.

Here's an example of a destructor in C#:
<pre>
public class MyClass
{
    ~MyClass()
    {
        // Release unmanaged resources
    }
}
</pre>
Finalize method:
The finalize method is a method that is called by the GC before an object is garbage collected. Like a destructor, the purpose of the finalize method is to release any unmanaged resources that the object may be holding. However, the finalize method is not guaranteed to be called, and its timing is non-deterministic.

Note: The C# compiler does not allow you to override the Finalize method. Instead, you provide a finalizer by implementing a destructor for your class.
Finally Block:
The finally block is a block of code that is guaranteed to be executed, regardless of whether an exception is thrown or not. The purpose of the finally block is to release any resources that may have been acquired in a try block.

Here's an example of a finally block in C#:
<pre>
try
{
    // Do something
}
catch (Exception ex)
{
    // Handle the exception
}
finally
{
    // Release resources
}
</pre>
In summary, while all three constructs deal with releasing resources, a destructor is used for objects and is called automatically by the GC, a finalize method is also used for objects, but is not guaranteed to be called, and a finally block is used for exception handling and is guaranteed to be executed.

-----------------------------------------------------------------------------------
### Q - What is the Garbge collector? (With)
Garbage Collector (GC) is a feature in many modern programming languages, including C#, Java, and Python, which automatically manages memory allocation and deallocation for an application. The purpose of the GC is to free the developer from the burden of manually managing memory, which can be error-prone and time-consuming.

The GC works by periodically scanning the heap (the memory space where objects are stored) to identify objects that are no longer being used by the application. These objects are marked as garbage and are eligible for collection. When the GC runs, it frees the memory occupied by the garbage objects and returns it to the system.

The GC in C# is a generational collector, meaning that it divides the heap into three generations: 0, 1, and 2. Newly created objects are placed in generation 0, and if they survive a GC cycle, they are promoted to generation 1, and so on. The GC also uses different algorithms, such as mark-and-sweep, reference counting, and compaction, to manage the heap efficiently.

Although the GC is generally reliable, it's important to note that it's not perfect. For example, it can't collect objects that have circular references or objects that use unmanaged resources, such as file handles or network connections. In these cases, it's necessary to manually release the resources, which can be done using destructors, finalizers, or by implementing the IDisposable interface.

Overall, the GC is a powerful tool that simplifies memory management for developers and reduces the risk of memory leaks and other memory-related issues

-----------------------------------------------------------------------------------
### Q - What's a seald class? (With)
In C#, a sealed class is a class that cannot be inherited by other classes. Once a class is marked as sealed, it can no longer serve as a base class for any other class.

Here's an example of a sealed class in C#:
<pre>
public sealed class MySealedClass
{
    // Class members go here
}
</pre>
In this example, the MySealedClass is marked as sealed using the sealed keyword. This means that no other class can inherit from it. If we try to create a class that inherits from MySealedClass, we will get a compile-time error:
<pre>
public class MyDerivedClass : MySealedClass // This will result in a compile-time error
{
    // Class members go here
}
</pre>
Sealing a class is often done for performance reasons, as it allows the compiler to optimize the class more aggressively. It can also be used to prevent unintended inheritance and to enforce a more strict object model.

It's worth noting that although a sealed class cannot be inherited, it can still implement interfaces, and it can still contain virtual methods that can be overridden by its own members.

-----------------------------------------------------------------------------------
### Q - What's a virtual key? (With)
In C#, a virtual key is a code that represents a physical key on a keyboard. Virtual keys are used to enable the processing of user input, such as keystrokes, mouse clicks, and touch events.

<pre>
using System;
using System.Windows.Forms;

namespace VirtualKeyExample
{
    class Program
    {
        static void Main(string[] args)
        {
            // Listen for key presses
            Console.WriteLine("Press any key to see its virtual key code");
            while (true)
            {
                ConsoleKeyInfo keyInfo = Console.ReadKey();
                int virtualKeyCode = (int)keyInfo.Key;
                Console.WriteLine("The virtual key code for {0} is {1}", keyInfo.Key, virtualKeyCode);
            }
        }
    }
}
</pre>
In this example, we use the Console.ReadKey() method to read input from the console. When the user presses a key, the Console.ReadKey() method returns a ConsoleKeyInfo object that contains information about the key that was pressed, including its virtual key code.

To get the virtual key code, we cast the Key property of the ConsoleKeyInfo object to an int value. This value represents the virtual key code of the key that was pressed.

Note that the System.Windows.Forms namespace also provides a Keys enumeration that contains constants for all the virtual keys on a standard keyboard. These constants can be used to simplify the handling of user input in Windows Forms applications.

For example, the following code demonstrates how to handle the KeyPress event of a TextBox control using the Keys enumeration:
<pre>
private void textBox1_KeyPress(object sender, KeyPressEventArgs e)
{
    if (e.KeyChar == (char)Keys.Enter)
    {
        // Handle Enter key press
    }
    else if (e.KeyChar == (char)Keys.Escape)
    {
        // Handle Escape key press
    }
}
</pre>
In this example, we use the Keys enumeration to compare the KeyPressEventArgs.KeyChar property to the virtual key codes for the Enter and Escape keys. If the user presses either of these keys while the TextBox control has focus, the appropriate event handler is called.


-----------------------------------------------------------------------------------
### Q - Difference between IEnumerable and IQueryable ?   (With)
In C#, IEnumerable and IQueryable are two interfaces that are commonly used with LINQ (Language-Integrated Query) to query and manipulate data. While both interfaces are used to represent a collection of data, they have some key differences in terms of their behavior and performance characteristics.

IEnumerable is the simpler of the two interfaces, and it is used to represent a sequence of data that can be enumerated. It defines a single method, GetEnumerator(), which returns an enumerator that can be used to iterate over the sequence.

Here's an example of how to use IEnumerable with LINQ:
<pre>
IEnumerable<string> fruits = new List<string> { "apple", "banana", "orange" };
IEnumerable<string> query = fruits.Where(fruit => fruit.StartsWith("a"));

foreach (string fruit in query)
{
    Console.WriteLine(fruit);
}
</pre>
In this example, we create an IEnumerable<string> collection of fruits and use the Where method to filter the collection based on a condition. The resulting sequence is stored in an IEnumerable<string> variable, and we use a foreach loop to iterate over the results and print them to the console.

IQueryable, on the other hand, is used to represent a query that can be executed against a data source, such as a database or a web service. It defines methods for building up a query, such as Where, OrderBy, and Select, but unlike IEnumerable, it does not execute the query immediately. Instead, it creates an expression tree that can be translated to the underlying data source and executed there.

Here's an example of how to use IQueryable with LINQ:
<pre>
IQueryable<Product> products = dbContext.Products;
IQueryable<Product> query = products.Where(p => p.Category == "Fruits");

foreach (Product product in query)
{
    Console.WriteLine(product.Name);
}
</pre>
In this example, we use an IQueryable<Product> collection to query a database of products. We use the Where method to filter the collection based on a condition, and the resulting expression tree is stored in an IQueryable<Product> variable. When we iterate over the results using a foreach loop, the query is executed against the database and only the matching products are returned.

The main advantage of using IQueryable over IEnumerable is that it allows queries to be executed on the server side, rather than fetching all the data and filtering it on the client side. This can result in significant performance gains for large datasets. However, it's important to note that not all LINQ providers support IQueryable, so it may not be available in all scenarios.

-----------------------------------------------------------------------------------
### Q - What's a record in C# 9?
C# 9 introduces a new feature called records, which are a simplified way to define classes that are primarily used to store data. Records provide a concise syntax for defining immutable objects with value semantics, and they can be used to reduce boilerplate code and improve the readability of your code.

Here's an example of how to define a record in C# 9:
<pre>
public record Person(string FirstName, string LastName, int Age);
</pre>
In this example, we define a record called Person that has three properties: FirstName, LastName, and Age. The record keyword indicates that this is a record type, and the parentheses define the properties of the record.

One of the key features of records is that they provide built-in support for value-based equality and hashing. This means that two records with the same property values will be considered equal, even if they are different objects. For example:
<pre>
var person1 = new Person("John", "Doe", 30);
var person2 = new Person("John", "Doe", 30);

Console.WriteLine(person1 == person2); // True
</pre>
In addition to providing built-in support for equality and hashing, records also generate several other methods and features automatically, including a constructor, deconstructor, ToString() method, and with expression. The with expression is particularly useful, as it allows you to create a new record based on an existing record with one or more properties changed. For example:
<pre>
var person1 = new Person("John", "Doe", 30);
var person2 = person1 with { Age = 31 };

Console.WriteLine(person1); // Person { FirstName = John, LastName = Doe, Age = 30 }
Console.WriteLine(person2); // Person { FirstName = John, LastName = Doe, Age = 31 }
</pre>
Overall, records are a powerful and convenient way to define simple classes that are primarily used to store data. They provide many features and benefits out-of-the-box, which can reduce the amount of boilerplate code you need to write and make your code more concise and readable.

-----------------------------------------------------------------------------------
### Q - What's the Difference between class and record in C# 9 ?
In C# 9, records are a new feature that provides a simplified syntax for defining classes that are primarily used to store data. While records share many similarities with classes, there are some key differences between the two.

Here are some of the main differences between classes and records in C# 9:

Mutability: By default, classes are mutable, which means that their properties can be changed after they are instantiated. Records, on the other hand, are immutable by default, which means that their properties cannot be changed after they are created. This makes records well-suited for modeling data that is not meant to be modified once it has been created.

Value-based equality: Records provide built-in support for value-based equality, which means that two records with the same property values are considered equal, even if they are different objects. Classes, on the other hand, do not provide built-in support for value-based equality and must implement the Equals() and GetHashCode() methods to achieve this behavior.

Built-in methods: Records generate several methods automatically, including a constructor, deconstructor, ToString() method, and with expression. Classes do not provide these methods out-of-the-box and must be implemented manually.

Inheritance: Records can inherit from other records or classes, but they cannot be inherited from. Classes can be inherited from and can also inherit from other classes.

Reference types: Classes are reference types, which means that their instances are allocated on the heap and their variables hold references to those instances. Records can be either reference types or value types, depending on their usage.

Overall, while records share many similarities with classes, they are primarily designed for modeling data that is not meant to be modified and can provide a more concise and readable way to define simple data structures. However, classes still have many advantages and may be more appropriate for more complex scenarios.

-----------------------------------------------------------------------------------
### Q - What is a delegate and an experssion in C# and how to use it?
In C#, a delegate is a type that represents a method signature. It can be used to reference methods as objects and pass them as parameters to other methods. An expression is a way of writing code that evaluates to a value. In C#, expressions can be used in a variety of contexts, such as assignment statements, method calls, and conditional statements.

Here's an example of using a delegate and expression in C#:

<pre>
using System;

delegate int MyDelegate(int x, int y);

class Program
{
    static int Add(int x, int y)
    {
        return x + y;
    }

    static void Main(string[] args)
    {
        MyDelegate del = new MyDelegate(Add);

        int result = del(5, 10);

        Console.WriteLine("Result = " + result);

        Func<int, int, int> expression = (x, y) => x + y;

        result = expression(5, 10);

        Console.WriteLine("Result = " + result);
    }
}
</pre>

In this example, we define a delegate called MyDelegate that takes two int parameters and returns an int value. We also define a method called Add that takes two int parameters and returns their sum.

In the Main method, we create a new instance of the MyDelegate delegate and initialize it with the Add method. We then invoke the delegate with the arguments 5 and 10 and assign the result to a variable called result.

We then print the value of result to the console. The output should be:

<pre>
Result = 15
</pre>

Next, we define an expression using the Func delegate, which is a built-in delegate that takes a specified number of input parameters and returns a value. In this case, the Func delegate takes two int parameters and returns an int value.

The expression we define is a lambda expression that takes two int parameters and returns their sum. We assign the expression to a variable called expression and then invoke it with the arguments 5 and 10 and assign the result to the result variable.

We then print the value of result to the console again. The output should be the same as before:

<pre>
Result = 15
</pre>
This example demonstrates how delegates and expressions can be used to encapsulate method calls and evaluate code at runtime. Delegates can be used to pass methods as parameters to other methods, while expressions can be used to define code that evaluates to a value.

---------------------------------------------------------------------------------------
### Q- Difference between Pass by refrence and pass by value? (With)
In C#, when passing an argument to a method, it can be done in two ways: "pass by reference" and "pass by value".

When an argument is passed by value, a copy of the argument is created and passed to the method, leaving the original argument unchanged. When an argument is passed by reference, a reference to the original argument is passed to the method, allowing the method to modify the original argument.

Here are examples of both pass by value and pass by reference in C#:

Pass by Value:
<pre>
static void Main(string[] args) {
    int a = 5;
    IncrementByValue(a);
    Console.WriteLine(a); // Output: 5
}

static void IncrementByValue(int b) {
    b++;
}
</pre>
In this example, the method IncrementByValue takes an integer argument b by value. The Main method initializes an integer a to 5 and calls the IncrementByValue method, passing in a. When IncrementByValue is called, a copy of the value of a is made and passed to the method. b is then incremented by 1, but the original value of a remains unchanged. When the program prints a to the console, it still outputs 5.

Pass by Reference:
<pre>
static void Main(string[] args) {
    int a = 5;
    IncrementByRef(ref a);
    Console.WriteLine(a); // Output: 6
}

static void IncrementByRef(ref int b) {
    b++;
}
</pre>
In this example, the method IncrementByRef takes an integer argument b by reference, indicated by the ref keyword. The Main method initializes an integer a to 5 and calls the IncrementByRef method, passing in a with the ref keyword. When IncrementByRef is called, a reference to the original value of a is passed to the method. b is then incremented by 1, modifying the original value of a. When the program prints a to the console, it now outputs 6.

-----------------------------------------------------------------------------------
### Q- What is the difference between assigning a reference type to another reference type and assigning a value type to another value type?
When working with objects in C#, it is important to understand the difference between reference types and value types.

Reference types are types that are stored in memory as a reference to an object, rather than as the actual value of the object. When you create a new instance of a reference type, a new object is created in memory, and a reference to that object is returned. Any variables that reference the same object will have the same value.

Value types, on the other hand, are types that are stored in memory as the actual value of the object, rather than as a reference to the object. When you create a new instance of a value type, a new copy of the object is created in memory. Any variables that reference the same value will have different memory locations.

Here's an example of creating reference and value types in C#:

<pre>
// Creating a reference type
class Person {
    public string Name { get; set; }
    public int Age { get; set; }
}

Person person1 = new Person { Name = "John", Age = 30 };
Person person2 = person1;

// Changing the value of a property in person1 also changes it in person2
person1.Name = "Jane";
Console.WriteLine(person2.Name); // Output: "Jane"


// Creating a value type
int x = 5;
int y = x;

// Changing the value of x does not affect the value of y
x = 10;
Console.WriteLine(y); // Output: 5
</pre>
In the above example, we create a reference type called Person and a value type called int. We then create two variables for each type, and assign the value of one variable to the other.

For the reference type Person, when we change the value of a property in person1, it also changes the value in person2, since they are both references to the same object.

For the value type int, when we change the value of x, it does not affect the value of y, since they are both separate values.

-----------------------------------------------------------------------------------
</br>

## **Database**
### Q- Lazy loading vs Eager Loading (With)
Lazy loading and eager loading are two approaches to loading data in a software system.

Lazy loading: Lazy loading is a technique in which data is loaded only when it is needed. In other words, data is loaded on demand, rather than being loaded all at once. This approach can improve performance and reduce memory usage, as only the necessary data is loaded into memory. However, lazy loading can also cause delays when the data is first accessed, as the system must retrieve the data from the database or other storage location.

Eager loading: Eager loading is a technique in which data is loaded in advance, before it is needed. In other words, all the necessary data is loaded into memory at once, even if some of it may not be used immediately. This approach can reduce delays when the data is first accessed, as the data is already loaded into memory. However, eager loading can also increase memory usage and reduce performance, as all the data is loaded at once, even if some of it may not be needed.

In general, the choice between lazy loading and eager loading depends on the specific requirements of the system. If the system needs to access large amounts of data frequently, lazy loading may be the better approach, as it can reduce memory usage and improve performance. On the other hand, if the system needs to access data quickly and predictably, eager loading may be the better approach, as it can reduce delays and improve response time.

-----------------------------------------------------------------------------------
</br>

### Q- Difference between these Queries: (With)
#### - Delete and drop 
#### - Drop and trunke  
#### - Where and having  
#### - Join and Unoin  
#### - UnUnion and Unoin  
#### - Not in and Not exist   
#### - What is DISTINCT  
Delete and drop:
Delete is a command used to remove rows from a table based on a specific condition. The data is removed from the table, but the table structure remains intact.
Drop is a command used to remove an entire table from the database. This removes both the table and its contents.

Drop and truncate:
Drop is a command used to remove an entire table from the database.
Truncate is a command used to remove all the rows from a table. Unlike drop, truncate does not remove the table itself.

Where and having:
Where is a clause used to filter rows based on a specific condition. It is used with the SELECT, UPDATE, and DELETE commands.
Having is a clause used to filter results based on a specific condition in a group. It is used with the GROUP BY clause.

Join and Union:
Join is a clause used to combine rows from two or more tables based on a related column between them.
Union is a command used to combine the results of two or more SELECT statements into a single result set, with duplicates removed.

Union and Union All:
Union is a command used to combine the results of two or more SELECT statements into a single result set, with duplicates removed.
Union All is a command used to combine the results of two or more SELECT statements into a single result set, with duplicates included.

Not in and Not exist:
Not in is a clause used to exclude rows from the result set that match a subquery.
Not exist is a clause used to exclude rows from the result set that do not match a subquery.

DISTINCT:
DISTINCT is a keyword used to remove duplicates from a result set. It is used in conjunction with the SELECT statement to return unique values from a column.

-----------------------------------------------------------------------------------
</br>

### What is Index? 
In the context of databases, an index is a data structure that is used to improve the speed of data retrieval operations on a table. An index can be thought of as a pointer to the location of data within a table, similar to the index at the back of a book that allows you to quickly find a specific page.

An index is created on one or more columns of a table and contains a sorted copy of the data in those columns, along with a pointer to the location of each row in the table that contains that data. When a query is executed that involves the indexed columns, the database can use the index to quickly find the rows that match the query criteria, rather than having to scan the entire table.

Indexes can greatly improve the performance of data retrieval operations, especially on large tables or tables with many columns. However, they also come with some overhead, as they require additional storage space and can slow down insert, update, and delete operations on the table.

In general, it is recommended to create indexes on columns that are frequently used in queries, such as primary key columns, foreign key columns, and columns used in WHERE or ORDER BY clauses. However, it is important to carefully balance the benefits and costs of indexes, as creating too many indexes or indexes on the wrong columns can actually decrease performance.

-----------------------------------------------------------------------------------
</br>

### Index Advanced? (With)
Advanced indexing is a technique used in databases to optimize queries that involve multiple conditions or complex expressions. Advanced indexing typically involves creating composite indexes, which are indexes that are created on multiple columns instead of just one.

Composite indexes are useful in situations where queries involve multiple conditions or expressions that reference different columns in a table. By creating an index that includes all of the relevant columns, the database can quickly locate the rows that match the query criteria, without having to scan the entire table.

In addition to composite indexes, there are several other advanced indexing techniques that can be used to optimize queries. These include:

Covering indexes: A covering index is an index that includes all of the columns referenced in a query, so that the database can satisfy the query entirely from the index, without having to access the table itself.

Partial indexes: A partial index is an index that includes only a subset of the rows in a table, based on a specified condition. This can be useful in situations where only a small percentage of the rows in a table are relevant to a particular query.

Function-based indexes: A function-based index is an index that is created on the result of a function or expression applied to a column. This can be useful in situations where queries involve complex expressions or calculations.

Overall, advanced indexing techniques are an important tool for optimizing database performance and improving the efficiency of queries. However, they require careful consideration and planning to ensure that they are used effectively and do not create unnecessary overhead.

-----------------------------------------------------------------------------------
</br>

### Index disadvanced? (With)
While indexes can provide significant performance benefits for queries, they can also have some disadvantages, including:

Increased storage requirements: Indexes require additional storage space to store the index data structures, which can be a significant consideration for large tables.

Increased maintenance overhead: Indexes must be maintained as data in the table changes, which can add overhead to database operations.

Decreased write performance: Indexes can slow down insert, update, and delete operations, since the database must update the index data structures in addition to the table data.

Index fragmentation: Over time, indexes can become fragmented, which can decrease their performance benefits and require additional maintenance operations to reorganize or rebuild the index.

Increased query complexity: Query plans that involve multiple indexes can become more complex, which can make query tuning more difficult and increase the risk of suboptimal query performance.

Overall, indexes are a valuable tool for optimizing query performance in databases, but they should be used judiciously and with consideration for their potential disadvantages. Database administrators should carefully evaluate the benefits and costs of creating indexes on tables, and regularly monitor and maintain existing indexes to ensure optimal performance.

-----------------------------------------------------------------------------------
</br>

### What is Clusterd and non Clusterd Index?  (With)
In a database, a clustered index and a non-clustered index are two types of indexes that can be created on a table to improve the performance of queries.

A clustered index determines the physical order of data in a table. When a clustered index is created on a table, the data in the table is physically reordered based on the values in the indexed column(s). This means that the data is stored in the order of the index, which allows for fast retrieval of data based on the index. A table can have only one clustered index, and it is usually created on the primary key column(s) of the table.

A non-clustered index is a separate data structure that contains a copy of the indexed column(s) along with a pointer to the location of each row in the table that contains that data. Unlike a clustered index, a non-clustered index does not determine the physical order of the data in the table. This means that a table can have multiple non-clustered indexes, and they can be created on any column(s) in the table.

When a query is executed that involves the indexed column(s), the database can use the clustered or non-clustered index to quickly find the rows that match the query criteria, rather than having to scan the entire table. However, the choice of whether to use a clustered or non-clustered index depends on the specific requirements of the system and the queries being executed. In general, clustered indexes are faster for queries that involve range searches or sorting, while non-clustered indexes are faster for queries that involve filtering or searching for specific values.

-----------------------------------------------------------------------------------
</br>

### Clusterd Index advanced and disadvanced ? (With)
Clustered indexes have some advantages and disadvantages compared to non-clustered indexes. Here are some of the advanced and disadvantaged of clustered indexes:

#### Advantages:

Improved query performance: Clustered indexes are faster for queries that return a range of values from the indexed column, since the data is physically stored in index order on disk.

Reduced disk I/O: Because the data is physically ordered on disk, queries that require a large number of rows can often be satisfied by reading fewer pages from disk.

No need for bookmark lookups: Because the clustered index contains all of the columns in the table, queries that require additional columns beyond those in the index do not require a separate lookup operation.

#### Disadvantages:

Slower write performance: Because data is physically ordered on disk based on the clustered index, insert and update operations may require the entire data page to be rewritten, which can be slower than non-clustered indexes.

Increased storage requirements: Clustered indexes require more storage space than non-clustered indexes, since they contain all of the columns in the table.

Fragmentation: Clustered indexes can become fragmented over time, which can reduce their performance benefits and require additional maintenance operations.

Limited flexibility: Changing the structure of a table with a clustered index can be more difficult, since the index is tied to the physical ordering of the data on disk.

Overall, clustered indexes can provide significant performance benefits for certain types of queries, but they require careful consideration and maintenance to ensure optimal performance. They are typically best suited for tables that are frequently queried and rarely updated, where the performance benefits outweigh the potential disadvantages.

-----------------------------------------------------------------------------------
</br>
 
### Non-Clusterd Index advanced and disadvanced ? (With)
Non-clustered indexes also have some advantages and disadvantages compared to clustered indexes. Here are some of the advanced and disadvantaged of non-clustered indexes:

#### Advantages:

Improved query performance: Non-clustered indexes can provide significant performance benefits for queries that return a subset of rows, or that require sorting or grouping.

Improved write performance: Non-clustered indexes typically require less overhead for insert and update operations, since they do not physically order the data on disk.

Reduced storage requirements: Non-clustered indexes can be smaller than clustered indexes, since they only store the indexed column data and a pointer to the associated table row.

Increased flexibility: Non-clustered indexes are not tied to the physical ordering of the data on disk, which makes them easier to create and maintain.

#### Disadvantages:

Increased disk I/O: Queries that require additional columns beyond those in the non-clustered index may require a separate lookup operation to retrieve the additional data from the table.

Increased maintenance overhead: Non-clustered indexes must be maintained as data in the table changes, which can add overhead to database operations.

Index fragmentation: Over time, non-clustered indexes can become fragmented, which can decrease their performance benefits and require additional maintenance operations to reorganize or rebuild the index.

Overall, non-clustered indexes can provide significant performance benefits for certain types of queries, and they offer greater flexibility and lower storage requirements than clustered indexes. However, they may require more maintenance overhead and can be slower for certain types of queries. As with clustered indexes, database administrators should carefully evaluate the benefits and costs of creating non-clustered indexes on tables, and regularly monitor and maintain existing indexes to ensure optimal performance.


-----------------------------------------------------------------------------------
</br>

### What is Normalization? 
Normalization is the process of organizing data in a database to eliminate redundancy and improve data integrity. The goal of normalization is to create tables that are well-structured, with each table containing only related data and each piece of data appearing only once.

Normalization is achieved through a series of steps, called normal forms. There are several normal forms, each with its own set of rules and requirements. The most commonly used normal forms are:

First Normal Form (1NF): In 1NF, each table has a primary key, and all data is atomic (i.e., indivisible). This means that there are no repeating groups of columns in a table.

Second Normal Form (2NF): In 2NF, all non-key columns in a table are dependent on the entire primary key. This means that there are no partial dependencies on the primary key.

Third Normal Form (3NF): In 3NF, all non-key columns in a table are dependent only on the primary key, and not on other non-key columns. This means that there are no transitive dependencies between non-key columns.

There are also higher normal forms, such as Boyce-Codd Normal Form (BCNF) and Fourth Normal Form (4NF), that further eliminate redundancy and improve data integrity.

Normalization is important because it helps ensure that data is consistent and accurate, and makes it easier to maintain and update the database. However, it is also important to balance normalization with performance considerations, as highly normalized tables can be more difficult to query efficiently. Therefore, a good database design should strive to achieve an appropriate level of normalization while also taking into account the specific requirements of the system.

-----------------------------------------------------------------------------------
</br>

### Q- What is stored procuder and when used it ?
A stored procedure is a precompiled collection of SQL statements that are stored in a database and can be executed as a single unit. Stored procedures are used to encapsulate frequently used database operations, such as inserting, updating, and retrieving data, into reusable code that can be called from multiple applications or client programs.

Stored procedures offer several advantages over ad hoc SQL statements:

Improved performance: Stored procedures are precompiled, which means they can execute faster than ad hoc SQL statements.

Improved security: Stored procedures can be granted permission to users or roles, which helps to control access to the underlying database objects.

Code reuse: Stored procedures can be reused across multiple applications or client programs, which can help to reduce development time and maintenance costs.

Simplified maintenance: Changes to a stored procedure can be made in a single location and will be immediately available to all applications or client programs that call it.

Here's an example of how to create a stored procedure in SQL Server:

<pre>
CREATE PROCEDURE dbo.GetCustomers
    @LastName NVARCHAR(50)
AS
BEGIN
    SET NOCOUNT ON;
    
    SELECT CustomerID, FirstName, LastName, Email
    FROM Customers
    WHERE LastName = @LastName;
END
</pre>
This stored procedure, called GetCustomers, takes a single parameter (@LastName) and returns a list of customers with that last name. To call the stored procedure from a client program or application, you would use the EXEC statement:

<pre>
EXEC dbo.GetCustomers @LastName = 'Smith';
</pre>
This would return a list of all customers with the last name "Smith". You can also pass in a different last name as the parameter to get a different set of results.

-----------------------------------------------------------------------------------
</br>

### Q- What is Function and when used it ?
In SQL, a function is a prewritten code block that can be called to perform a specific task. Functions are similar to stored procedures, but they return a value or a table rather than executing a series of statements.

Functions are useful in situations where you need to perform a specific calculation or transformation on a set of data, and want to reuse that code across multiple queries or applications.

Here's an example of how to create a simple function in SQL Server:

<pre>
CREATE FUNCTION dbo.AddNumbers
(
    @Num1 INT,
    @Num2 INT
)
RETURNS INT
AS
BEGIN
    DECLARE @Result INT;
    SET @Result = @Num1 + @Num2;
    RETURN @Result;
END
</pre>
This function, called AddNumbers, takes two integer parameters (@Num1 and @Num2) and returns their sum as an integer. To call the function from a query or application, you would use it in a select statement like this:

<pre>
SELECT dbo.AddNumbers(2, 3);
</pre>
This would return the value 5. You can also use variables or column values as the parameters to the function. For example:

<pre>
DECLARE @Num1 INT = 2;
DECLARE @Num2 INT = 3;
SELECT dbo.AddNumbers(@Num1, @Num2);
</pre>
This would also return the value 5. Functions can be used in a wide variety of scenarios, from simple arithmetic calculations to more complex data transformations and validations.

-----------------------------------------------------------------------------------
</br>

### Q- Stored procuder vs Function ?
Stored procedures and functions are both prewritten code blocks in SQL, but they differ in their purpose and usage.

Stored procedures are used to encapsulate a series of SQL statements or operations into a reusable code block that can be called from multiple applications or client programs. Stored procedures can have input and output parameters, and can return multiple result sets or update data in the database.

Functions, on the other hand, are used to perform a specific calculation or transformation on a set of data, and return a single value or table. Functions can be used in SQL statements such as SELECT, WHERE, and HAVING clauses to transform data and return specific results.

Here are some key differences between stored procedures and functions:

Return type: Stored procedures do not have a return type, but can modify the database by inserting, updating or deleting data. Functions return a single value or table.

Usage: Stored procedures are typically used to perform operations that modify the database, such as updating data or executing a series of statements. Functions are used to perform calculations or transformations on data, and are typically used in SQL queries.

Input and output: Stored procedures can have input and output parameters, and can return multiple result sets. Functions also have input parameters, but can only return a single value or table.

Reusability: Stored procedures can be called from multiple applications or client programs, which helps to reduce development time and maintenance costs. Functions can also be used in multiple queries or statements, but are typically used for more specific calculations or transformations.

In general, stored procedures are used for more complex database operations, while functions are used for more specific data transformations or calculations. Both stored procedures and functions are useful in different scenarios, and can help to improve the efficiency and maintainability of SQL code.

-----------------------------------------------------------------------------------
</br>

### Q- What is constraint?
In SQL, a constraint is a rule or restriction that is applied to a table column or a group of columns. Constraints help to ensure data integrity and consistency by preventing invalid or inconsistent data from being inserted or updated in the table.

Here are some commonly used constraints in SQL:

NOT NULL: This constraint specifies that a column cannot contain null values.

UNIQUE: This constraint ensures that each value in a column is unique and cannot be duplicated.

PRIMARY KEY: This constraint is used to uniquely identify each row in a table, and can be defined on one or more columns.

FOREIGN KEY: This constraint is used to establish a relationship between two tables, and ensures that data inserted into the foreign key column matches the values in the referenced primary key column.

CHECK: This constraint specifies a condition that must be satisfied for data to be inserted or updated in the column.

Constraints can be defined when a table is created, or they can be added later using the ALTER TABLE statement. Constraints help to ensure data integrity and consistency, and can help to prevent data errors and inconsistencies in the database.

-----------------------------------------------------------------------------------
</br>

### Q- What is Trigger?
In SQL, a trigger is a special type of stored procedure that is automatically executed in response to certain database events, such as an insert, update, or delete operation on a table. Triggers can be used to enforce business rules, audit changes to data, or perform complex data transformations.

Triggers are defined on a specific table or view, and are automatically executed before or after the database operation that triggers them. For example, a trigger can be defined to execute before an insert operation, to validate the data being inserted and enforce certain business rules. Similarly, a trigger can be defined to execute after an update operation, to perform some additional data transformation or to update other tables in the database.

Triggers can be defined to execute once for each row affected by the triggering operation, or once for each statement that triggers them. Triggers can also be disabled or enabled using the ALTER TABLE statement, which can be useful for debugging or troubleshooting.

Here are some common uses for triggers in SQL:

Enforcing business rules: Triggers can be used to enforce business rules or constraints, such as preventing certain types of data from being inserted or updated.

Auditing changes: Triggers can be used to record changes to data in a separate audit table, which can be useful for tracking changes and performing data analysis.

Complex data transformations: Triggers can be used to perform complex data transformations, such as calculating derived values or updating related tables.

Replication: Triggers can be used to replicate data to other databases or systems, such as in a distributed database environment.

Overall, triggers are a powerful feature of SQL that can be used to automate complex business logic and enforce data integrity and consistency in the database. However, triggers should be used carefully and sparingly, as they can have a significant impact on database performance and can be difficult to debug and maintain.

-----------------------------------------------------------------------------------
</br>

### Q-What is CTE?
In SQL, a Common Table Expression (CTE) is a temporary named result set that can be referenced within a single SQL statement. CTEs are similar to subqueries, but provide a more flexible and reusable way to define intermediate result sets that can be used multiple times within a single query.

CTEs are defined using the WITH keyword, followed by a name for the CTE and a SELECT statement that defines the result set. The CTE can then be referenced in subsequent queries using its name, as if it were a table.

One of the key advantages of CTEs is that they can be used to simplify complex queries and make them more readable and maintainable. For example, a CTE can be used to define a set of common filtering or aggregation criteria that can be reused throughout a larger query.

Another advantage of CTEs is that they can improve query performance by allowing the database engine to optimize and reuse the intermediate result sets defined in the CTE.

Here's an example of how a CTE can be used to simplify a complex query:

<pre>
WITH sales_by_region AS (
  SELECT region, SUM(sales) AS total_sales
  FROM sales_table
  GROUP BY region
)

SELECT region, total_sales
FROM sales_by_region
WHERE total_sales > 100000
</pre>
In this example, the CTE sales_by_region is defined as the total sales by region, and is then referenced in the subsequent query to filter results where the total sales exceed a certain threshold.

-----------------------------------------------------------------------------------
</br>

### Q-What is View?
In SQL, a view is a virtual table that is defined by a SQL query. Unlike physical tables, views do not contain any data themselves, but instead provide a way to query and present data from one or more underlying tables or views.

Views can be used to simplify complex queries by providing a pre-defined subset of data that is tailored to a specific use case or application. For example, a view could be created to show only the most recent orders from a customer, or to summarize sales data by region or product category.

Views can also be used to provide a more secure and controlled way to access data, by limiting the columns or rows that are visible to certain users or applications. By defining a view with only the necessary columns and rows, it is possible to prevent unauthorized access to sensitive data.

Creating a view in SQL is typically done using a CREATE VIEW statement, followed by a SELECT statement that defines the query used to populate the view. Here's an example:

<pre>
CREATE VIEW customer_orders AS
SELECT customer_name, order_date, order_total
FROM customers
JOIN orders ON customers.customer_id = orders.customer_id
</pre>

In this example, a view called customer_orders is created that joins the customers and orders tables to create a virtual table that includes the customer name, order date, and order total. Once the view is created, it can be queried like any other table using a SELECT statement.

-----------------------------------------------------------------------------------
</br>

### Q-What is isolations levels?

In database management systems, isolation levels are a set of rules that determine how transactions interact with each other and with the underlying data. Isolation levels define the degree to which one transaction must be isolated from other transactions and how the changes made by one transaction can be seen by other transactions.

There are several isolation levels defined by the ANSI/ISO SQL standard, and most relational database management systems support at least some of them. The most common isolation levels are:

Read Uncommitted: The lowest isolation level, where transactions can see uncommitted changes made by other transactions.

Read Committed: Transactions can only see committed changes made by other transactions.

Repeatable Read: Transactions are guaranteed to see the same data throughout the transaction, even if other transactions make changes to the data.

Serializable: The highest isolation level, where transactions are completely isolated from each other, and appear to be executed one after the other.

Snapshot: A non-standard isolation level, where each transaction sees a snapshot of the data at the beginning of the transaction, and any changes made by other transactions are ignored.

The choice of isolation level depends on the specific requirements of the application and the database. Higher isolation levels provide greater transaction safety, but also reduce concurrency and can lead to increased blocking and reduced performance. Lower isolation levels can provide higher concurrency and better performance, but may lead to data inconsistencies and concurrency problems.

It is important for developers and database administrators to understand the various isolation levels and choose the appropriate one for their application to ensure that transactions are processed correctly and data integrity is maintained.

-----------------------------------------------------------------------------------
</br>

## **Solid Principle:**
### What's SOLID principle? (With)
SOLID is a set of principles for object-oriented programming that aim to make software systems more maintainable, scalable, and easy to extend. The five SOLID principles are:

Single Responsibility Principle (SRP): This principle states that a class should have only one reason to change. In other words, a class should have only one responsibility, and any change to that responsibility should require only one change to the class.

Open/Closed Principle (OCP): This principle states that a class should be open for extension but closed for modification. In other words, new functionality should be added to a system by adding new code, rather than modifying existing code.

Liskov Substitution Principle (LSP): This principle states that objects of a superclass should be able to be replaced with objects of a subclass without affecting the correctness of the system.

Interface Segregation Principle (ISP): This principle states that clients should not be forced to depend on interfaces they do not use. In other words, interfaces should be designed to be specific to the needs of the clients that use them.

Dependency Inversion Principle (DIP): This principle states that high-level modules should not depend on low-level modules, but both should depend on abstractions. In other words, the code should depend on abstractions, rather than on concrete implementations.

Together, these principles promote good design practices that can lead to more maintainable, scalable, and extensible software systems. By following these principles, developers can create code that is easier to understand, modify, and extend over time.

https://www.youtube.com/watch?v=-hbWDYRSjqk&list=PLnqAlQ9hFYdflFSS4NigVB7aSoYPNwHTL 

-----------------------------------------------------------------------------------
</br>

## **Design patterns:**
### Q- What's Design Pattern? (With)
A design pattern is a general reusable solution to a commonly occurring problem within a particular context in software design. It is a description or template for how to solve a particular problem that can be adapted and reused in different situations. Design patterns are like templates or blueprints for building software that help developers solve common problems in an efficient and effective way.

Design patterns can be categorized into three main groups: creational, structural, and behavioral. Creational patterns are concerned with object creation mechanisms, trying to create objects in a manner suitable to the situation. Structural patterns deal with object composition, forming class hierarchies, and defining how objects are composed to form larger structures. Behavioral patterns are concerned with communication between objects, encapsulating behaviors and interactions between objects.

The use of design patterns can provide several benefits, such as reducing the time and effort needed to solve common problems, improving code readability and maintainability, facilitating communication between team members, and promoting code reusability. There are many well-known design patterns, such as the Singleton pattern, Factory pattern, Observer pattern, Decorator pattern, and many more.
<small>
By understanding and applying design patterns, developers can create more robust, maintainable, and extensible software that can better meet the needs of their users. However, it's important to note that design patterns should be used judiciously and only where appropriate. Overuse or misuse of design patterns can lead to unnecessarily complex and difficult-to-maintain code.
</small>
-----------------------------------------------------------------------------------
</br>

### Q- What's Repository Pattern?

The Repository Pattern is a design pattern used in software engineering that helps to separate the logic that retrieves data from the underlying data source from the business logic that manipulates that data.
The primary goal of this pattern is to create an abstraction layer between the application's business logic and data access layer, making it easier to maintain, test and modify the application's codebase.
In this pattern, each entity in the application has a corresponding repository class that is responsible for performing operations on the data source. The repository class is responsible for querying the data source, mapping the data to domain objects, and providing a clean interface to the rest of the application to interact with the data.
This pattern allows developers to modify the underlying data source without affecting the application's business logic, as long as the repository interface remains unchanged. For instance, switching from a SQL database to a NoSQL database would require changing only the implementation of the repository, while the application code that interacts with the repository remains the same.
The repository pattern also facilitates testing by allowing developers to mock the data access layer during unit testing. It also helps to keep the business logic decoupled from the data access code, which promotes code reuse, reduces coupling and increases maintainability.
Overall, the repository pattern is a widely used approach that promotes separation of concerns and provides a flexible and scalable architecture for software applications.

-----------------------------------------------------------------------------------
</br>

### Q- What's Unit of work Pattern?
-Unit of work Pattern : 

The Unit of Work Pattern is a design pattern used in software engineering to manage database transactions and simplify the interaction between the application's business logic and the data access layer.

The primary goal of this pattern is to create a higher-level abstraction that encapsulates the database transaction and provides a consistent interface to the application for performing CRUD (Create, Read, Update, Delete) operations on the data.

In this pattern, the Unit of Work (UoW) is a single object that tracks changes made to the entities of the application and ensures that these changes are committed to the database in a single transaction. The UoW contains methods for adding, updating, and deleting entities, as well as a commit method that triggers the database transaction.

The UoW pattern is often used in conjunction with the Repository Pattern. The repository classes communicate with the UoW object to register changes to entities, and the UoW object coordinates these changes to ensure that they are committed to the database in a single transaction.

Using the UoW pattern provides several benefits, including:

1. Improved performance: By batching multiple CRUD operations into a single transaction, the UoW pattern can reduce the number of round trips to the database, resulting in improved performance.
2. Consistent data access: The UoW pattern ensures that all operations on the database are performed in a consistent manner and that the data is always in a valid state.
3. Simplified business logic: By encapsulating the transaction management and data access logic, the UoW pattern simplifies the application's business logic, making it easier to maintain and test.

Overall, the Unit of Work Pattern is a powerful tool for managing database transactions and simplifying data access in software applications. It provides a clean interface to the application for performing CRUD operations on the data, while also ensuring that the data remains consistent and in a valid state.

-----------------------------------------------------------------------------------
</br>

### Q- What's Dependency injection Pattern?
Dependency Injection (DI) is a software design pattern used in object-oriented programming to remove dependencies between classes and make code more modular, testable and maintainable.

The basic idea of DI is that instead of creating objects within a class that depend on other objects, those dependencies are provided from outside of the class. This means that the class no longer needs to be tightly coupled with the objects it uses, allowing for greater flexibility and easier testing.

In the DI pattern, dependencies are typically injected into a class through its constructor or by using setter methods. When the class is created, it is provided with the necessary dependencies, which it can use to perform its functions.

One of the main benefits of using DI is that it makes code more testable. By injecting dependencies into a class, it becomes much easier to mock or replace those dependencies with test doubles during unit testing. This allows for greater isolation of the code being tested and more accurate test results.

Another benefit of DI is that it makes code more modular and maintainable. By separating the creation of objects from their use, code becomes less tightly coupled and easier to modify. Changes to one part of the codebase are less likely to affect other parts of the codebase, which can make maintenance and updates much easier.

Overall, Dependency Injection is a powerful tool for creating more modular, testable, and maintainable code. By separating the creation of objects from their use, it helps to reduce coupling between classes and improve the flexibility and scalability of software applications.

[https://www.youtube.com/watch?v=YO4MGNu2xvI](https://www.youtube.com/watch?v=YO4MGNu2xvI)


#### Three ways to implement Dependency injection ? 
To add Dependency Injection (DI) to a program file, you typically need to follow these general steps:
Identify the dependencies of your class or component. This includes any external objects, libraries, or services that are needed for the class to function.
Create an interface or abstraction for the dependencies, if needed. This allows for more flexibility in substituting different implementations of the dependencies later on.
Configure the DI container to provide the necessary dependencies. This typically involves registering the dependencies with the container, specifying their lifetimes and scoping, and resolving any dependencies they might have.
Inject the dependencies into the class or component that requires them. This can be done using one of the three approaches mentioned earlier - constructor injection, setter injection, or interface injection.
Regarding the lifetime and scope of objects, there are generally three options to consider:

Transient: This creates a new instance of the object every time it is requested from the container. This is useful for objects that are stateless and can be safely recreated on each request.

Singleton: This creates a single instance of the object and reuses it for all requests. This is useful for objects that are expensive to create or maintain and should be shared across the application.

Scoped: This creates an instance of the object for a specific scope or context, such as a web request or a user session. This ensures that objects are properly managed and disposed of when no longer needed.

In summary, to add DI to a program file, you need to identify dependencies, configure the container, and inject dependencies using one of the available approaches. Additionally, you can specify the lifetime and scope of objects based on the needs of the application.

-----------------------------------------------------------------------------------
</br>

### Q- What's CQRS Pattern?
CQRS (Command Query Responsibility Segregation) is a pattern in software architecture that separates the responsibilities of the data model into two distinct parts: commands, which modify data, and queries, which retrieve data.

In a CQRS system, the data model is divided into two separate models: the write model, which is responsible for processing commands and modifying the data, and the read model, which is responsible for processing queries and retrieving the data. This separation of responsibilities allows the write and read models to be optimized for their specific tasks, leading to improved performance and scalability.

The key benefits of using CQRS are:

1. Improved performance: By separating the read and write models, each model can be optimized for its specific task, leading to improved performance.
2. Scalability: The read model can be easily scaled horizontally to handle an increase in read traffic, while the write model can be scaled vertically to handle an increase in write traffic.
3. Flexibility: CQRS allows for different representations of the data model to be used for different purposes, such as optimized views for specific use cases or support for different data storage technologies.
4. Better maintenance: By separating the responsibilities of the data model into distinct parts, it becomes easier to maintain and evolve the system over time.

CQRS is often used in combination with event sourcing, a pattern in which all changes to the data model are captured as a series of events, rather than just a snapshot of the current state. This combination provides a powerful way to build scalable and flexible systems that can handle complex data models and business requirements.

[https://code-maze.com/cqrs-mediatr-in-aspnet-core/](https://code-maze.com/cqrs-mediatr-in-aspnet-core/)

-----------------------------------------------------------------------------------
</br>

### Q-Mediator Pattern:
The Mediator Pattern is a behavioral design pattern that promotes loose coupling among objects by controlling the interactions between them. It allows objects to communicate with each other through a mediator object, instead of communicating directly with each other. The mediator object acts as an intermediary between the objects and manages their interactions.

In the Mediator Pattern, each object that needs to communicate with other objects has a reference to the mediator object. When an object needs to communicate with another object, it sends a message to the mediator object, which then forwards the message to the appropriate object.

The key benefits of the Mediator Pattern include:

Decoupling: The Mediator Pattern promotes loose coupling among objects, as they do not need to know about each other, but only about the mediator object.

Reusability: The Mediator Pattern allows for the reuse of mediator objects in different contexts, which can reduce code duplication and improve maintainability.

Extensibility: The Mediator Pattern allows for easy extension of the system, as new objects can be added without affecting the existing objects.

Centralized control: The Mediator Pattern provides a centralized control mechanism for managing the interactions among objects, which can improve the overall organization of the system.

Overall, the Mediator Pattern is a useful pattern for managing complex interactions among objects in a software system. It can promote loose coupling, improve maintainability and extensibility, and provide a centralized control mechanism for managing object interactions.

-----------------------------------------------------------------------------------
</br>

### Q-Facade Pattern?
The Facade pattern is a design pattern in software engineering that provides a simplified interface to a complex system of classes, functions, and interfaces. The purpose of the Facade pattern is to hide the complexity of the system and provide a simple and easy-to-use interface for clients.

The Facade pattern is used when you have a complex system with a large number of components, and you want to provide a simpler interface for clients to use. Instead of exposing all the details of the system, you create a facade that encapsulates the complexity and provides a simplified interface.

The Facade pattern consists of the following components:

Facade: This is the simplified interface that clients use to access the system. It provides a higher-level abstraction of the system and hides the complexity of the components.

Subsystems: These are the components that make up the system. They are the individual classes, functions, and interfaces that provide the functionality of the system.

The Facade pattern provides several benefits:

Simplified interface: By providing a simplified interface to a complex system, the Facade pattern makes it easier for clients to use the system.

Improved maintainability: By hiding the complexity of the system behind a facade, the Facade pattern makes the system easier to maintain and modify.

Reduced coupling: The Facade pattern reduces coupling between the client and the subsystem, making it easier to replace or modify components of the system without affecting the clients.

Improved performance: By providing a simplified interface and reducing the number of calls to the subsystem, the Facade pattern can improve performance.

In summary, the Facade pattern is a useful design pattern in software engineering that provides a simplified interface to a complex system. By hiding the complexity of the system behind a facade, the Facade pattern improves maintainability, reduces coupling, and provides a simpler and more intuitive interface for clients.

-----------------------------------------------------------------------------------
</br>

### Q-Proxy Pattern?
The Proxy pattern is a design pattern in software engineering that provides a surrogate or placeholder for another object to control access to it. The purpose of the Proxy pattern is to provide a layer of indirection between clients and an object, allowing for additional functionality to be added without changing the object's interface.

The Proxy pattern is used when you want to control access to an object or add additional functionality to an object's methods without changing the object's interface. The Proxy pattern consists of the following components:

Subject: This is the interface that the client interacts with. It defines the methods that the client can call on the object.

Real Subject: This is the actual object that the client wants to use. It implements the methods defined in the Subject interface.

Proxy: This is the object that controls access to the Real Subject. It implements the same interface as the Real Subject, and it intercepts calls from the client to the Real Subject.

The Proxy pattern provides several benefits:

Control access to an object: The Proxy pattern allows you to control access to an object by limiting the methods that the client can call on the object.

Add additional functionality: The Proxy pattern allows you to add additional functionality to an object's methods without changing the object's interface.

Improved performance: The Proxy pattern can improve performance by delaying the creation of an object until it is actually needed.

Improved security: The Proxy pattern can improve security by controlling access to sensitive objects.

In summary, the Proxy pattern is a useful design pattern in software engineering that provides a layer of indirection between clients and objects. By controlling access to objects and adding additional functionality to their methods, the Proxy pattern can improve performance, security, and maintainability.

-----------------------------------------------------------------------------------
</br>

### Q-Difference between Proxy Pattern and Facade Pattern?
Although both the Proxy pattern and the Facade pattern provide a layer of abstraction between the client and an underlying system, they serve different purposes.

The Facade pattern provides a simplified interface to a complex system, while the Proxy pattern provides a surrogate or placeholder for another object to control access to it.

The Facade pattern is used when you want to provide a simplified interface to a complex system of classes, functions, and interfaces. It encapsulates the complexity of the system and provides a higher-level abstraction of it to clients. The Facade pattern is typically used to improve the ease of use, maintainability, and flexibility of the system.

On the other hand, the Proxy pattern is used when you want to control access to an object or add additional functionality to an object's methods without changing the object's interface. It provides a layer of indirection between clients and an object, allowing you to limit access to the object or modify its behavior.

In summary, the main difference between the Proxy pattern and the Facade pattern is that the Proxy pattern provides a surrogate or placeholder for another object to control access to it, while the Facade pattern provides a simplified interface to a complex system.

-----------------------------------------------------------------------------------
</br>

### Q-Observal Pattern?
The Observer pattern is a design pattern in software engineering that allows objects to be notified of changes to the state of other objects without being tightly coupled to them. The purpose of the Observer pattern is to define a one-to-many dependency between objects, so that when one object changes its state, all its dependent objects are notified and updated automatically.

The Observer pattern consists of the following components:

Subject: This is the object that is being observed. It maintains a list of its dependent objects (called observers), and notifies them automatically when its state changes.

Observer: This is the object that is notified of changes to the state of the subject. It implements a method that is called by the subject when its state changes.

The Observer pattern provides several benefits:

Loose coupling: The Observer pattern reduces coupling between the subject and its observers, allowing them to be changed independently of each other.

Easy extensibility: The Observer pattern makes it easy to add new observers to the subject, allowing for easy extensibility of the system.

Easy debugging: The Observer pattern makes it easy to debug the system, as changes to the state of the subject can be traced through the observers.

Improved maintainability: The Observer pattern improves maintainability by reducing the complexity of the system and making it easier to modify.

In summary, the Observer pattern is a useful design pattern in software engineering that allows objects to be notified of changes to the state of other objects without being tightly coupled to them. By defining a one-to-many dependency between objects, the Observer pattern reduces coupling, improves maintainability, and makes it easy to extend and debug the system.

-----------------------------------------------------------------------------------
</br>

### Q-Staretgy pattern
The Strategy pattern is a behavioral design pattern in object-oriented programming that allows you to define a family of algorithms, encapsulate each one as an object, and make them interchangeable. This pattern enables the behavior of an object to be selected at runtime, without the client code having to know the details of how that behavior is implemented.

The Strategy pattern typically consists of three main components:

Context: This is the object that needs to perform a particular behavior, and it contains a reference to a Strategy object.

Strategy: This is an interface or abstract class that defines the behavior that needs to be performed.

Concrete Strategy: These are the classes that implement the Strategy interface, and provide a specific implementation of the behavior.

By using the Strategy pattern, you can easily switch between different algorithms or behaviors at runtime, without having to modify the code of the Context object. This makes the code more flexible and easier to maintain, since each behavior is encapsulated within a separate object. The Strategy pattern is commonly used in scenarios where you have multiple variations of a particular algorithm, and you need to select the appropriate one dynamically based on some runtime condition.

-----------------------------------------------------------------------------------
</br>

### Q-Factory pattern
 The Factory pattern is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. This pattern is useful when you want to create objects without exposing the instantiation logic to the client code, and also when you want to centralize object creation in a single location to simplify the code.

The Factory pattern typically consists of the following components:

Creator: This is an abstract class or interface that declares the factory method, which returns an object of a product type.

Concrete Creator: These are the classes that implement the factory method and create the product objects.

Product: This is the interface or abstract class that defines the type of object that will be created by the factory method.

Concrete Product: These are the classes that implement the Product interface, and provide a specific implementation of the product.

Using the Factory pattern, the client code only interacts with the Creator class, and does not have to know about the concrete product classes. The Creator class encapsulates the object creation process, and delegates it to the Concrete Creator classes based on some condition. This allows the client code to be decoupled from the object creation process, and also makes it easier to add new products or change the object creation process in the future.

Overall, the Factory pattern provides a flexible way to create objects, and is commonly used in scenarios where the client code needs to create objects dynamically at runtime, or when the creation of objects is complex and needs to be abstracted away from the client code.

-----------------------------------------------------------------------------------
</br>

### Q-Abstract factory pattern 
The Abstract Factory pattern is a creational design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes. This pattern is useful when you want to create multiple objects that are related or dependent on each other, and you want to ensure that they are created in a consistent way.

The Abstract Factory pattern typically consists of the following components:

Abstract Factory: This is an abstract class or interface that declares a set of factory methods for creating related or dependent objects.

Concrete Factory: These are the classes that implement the Abstract Factory interface and create the related or dependent objects.

Abstract Product: This is an abstract class or interface that declares the common interface for a set of related or dependent products.

Concrete Product: These are the classes that implement the Abstract Product interface and provide a specific implementation of the product.

Using the Abstract Factory pattern, the client code only interacts with the Abstract Factory and Abstract Product interfaces, and does not have to know about the concrete classes. The Abstract Factory encapsulates the creation of related or dependent objects, and delegates it to the Concrete Factory classes based on some condition. This allows the client code to be decoupled from the object creation process, and also makes it easier to add new products or change the object creation process in the future.

Overall, the Abstract Factory pattern provides a flexible way to create families of related or dependent objects, and is commonly used in scenarios where the client code needs to create objects dynamically at runtime, or when the creation of objects is complex and needs to be abstracted away from the client code.

-----------------------------------------------------------------------------------
</br>

## **Software Architecture**
### Q-Difference between Architecture and design pattern?
Architecture and design patterns are related concepts in software development, but they refer to different things.

Architecture refers to the overall structure of a software system, including its components, their interactions, and how they are organized to achieve specific goals. Architecture defines the high-level decisions that determine how the system will be built and how it will operate. Examples of software architectures include client-server, microservices, and event-driven architectures.

On the other hand, design patterns are reusable solutions to common problems that arise in software design. A design pattern describes a general solution to a recurring problem that can be applied in different contexts. Design patterns provide developers with proven solutions that have been used in real-world applications, and can help to improve the quality, maintainability, and extensibility of software systems. Examples of design patterns include the Singleton, Observer, and Factory patterns.

In summary, architecture refers to the overall structure of a software system, while design patterns provide specific solutions to common design problems within that structure.

-----------------------------------------------------------------------------------
</br>

### Q-Onion Architecture?
Onion Architecture is a software architecture pattern that emphasizes separation of concerns and modular design. It was introduced by Jeffrey Palermo in 2008 as an alternative to traditional layered architecture.

In Onion Architecture, the core business logic of the application is encapsulated in the center of the architecture, like the core of an onion, while the outer layers are responsible for interacting with the outside world, such as user interfaces, databases, and external services.

The layers of Onion Architecture are organized in a concentric circle around the core, with the innermost layer containing the most important business logic, and the outermost layer containing the least important or infrastructure-related logic.

The key benefits of Onion Architecture include:

Testability: The separation of concerns makes it easier to write unit tests and integration tests.

Maintainability: Changes to one layer do not affect other layers, making it easier to make modifications without affecting the entire system.

Flexibility: The modular design of Onion Architecture allows for easy integration of new features and components.

Independence: The layers of Onion Architecture are independent of each other, allowing for parallel development and deployment.

Overall, Onion Architecture is a useful pattern for building scalable, maintainable, and testable software systems.

-----------------------------------------------------------------------------------
</br>

### Q-Layres in onion architecture
In Onion Architecture, the layers are organized in a concentric circle around the core, with the innermost layer containing the most important business logic, and the outermost layer containing the least important or infrastructure-related logic. Here are the layers typically used in Onion Architecture:

Core: This is the center of the architecture, where the most important business logic is located. The Core layer is independent of the other layers, and contains the entities, business rules, and interfaces that define the application's behavior.

Domain: This layer contains the application-specific business logic, which is independent of the technical details of the system. The Domain layer defines the behavior of the application, and interacts with the Core layer to perform the necessary operations.

Application: This layer contains the use cases of the application, which define how the user interacts with the system. The Application layer orchestrates the interaction between the user and the Domain layer, and contains the application-specific logic that is not part of the business logic.

Infrastructure: This layer contains the technical details of the system, such as the database, web frameworks, and external services. The Infrastructure layer provides the necessary implementations for the interfaces defined in the Core and Domain layers.

Overall, the Onion Architecture layers are organized in a way that emphasizes the separation of concerns and the independence of the business logic from the technical details of the system. This helps to create software systems that are scalable, maintainable, and testable, while also being adaptable to changing business requirements and technical details.

-----------------------------------------------------------------------------------
</br>

### Q-Clean Architecture?
Clean Architecture is a software architecture pattern that focuses on the separation of concerns and the independence of the business logic from the technical details of the system. It was introduced by Robert C. Martin, also known as Uncle Bob, in 2012 as a way to create modular, maintainable, and testable software systems.

In Clean Architecture, the system is organized into concentric circles, with the innermost circle containing the most important and high-level business logic, and the outermost circle containing the low-level technical details of the system, such as databases, web frameworks, and third-party libraries. The circles are organized in layers, with each layer having its own set of responsibilities and dependencies.

The key benefits of Clean Architecture include:

Testability: The separation of concerns and the independence of the business logic make it easier to write unit tests and integration tests.

Maintainability: The modular design of Clean Architecture allows for easy maintenance and updates without affecting the entire system.

Flexibility: The independence of the business logic from the technical details of the system allows for easy integration of new features and components.

Scalability: The separation of concerns and the modular design of Clean Architecture allow for easy scaling of the system.

Overall, Clean Architecture is a useful pattern for building software systems that are scalable, maintainable, and testable, while also being adaptable to changing business requirements and technical details.

-----------------------------------------------------------------------------------
</br>

### Q-Layres in Clean architecture

In Clean Architecture, the layers are organized in a way that emphasizes the separation of concerns and the independence of the business logic from the technical details of the system. Here are the layers typically used in Clean Architecture:

Entities: This layer contains the business entities, such as objects or data structures, that represent the core business logic of the application. The Entities layer defines the behavior and data of the application, and is independent of the other layers.

Use Cases: This layer contains the application-specific business logic, which defines how the user interacts with the system. The Use Cases layer defines the behavior of the application, and interacts with the Entities layer to perform the necessary operations.

Interface Adapters: This layer contains the adapters that translate data between the Use Cases and the Infrastructure layers. The Interface Adapters layer defines the communication protocols and data transfer objects that allow the application to communicate with external systems and services.

Infrastructure: This layer contains the technical details of the system, such as databases, web frameworks, and external services. The Infrastructure layer provides the necessary implementations for the interfaces defined in the Interface Adapters and Use Cases layers.

Overall, the Clean Architecture layers are organized in a way that emphasizes the independence of the business logic from the technical details of the system, and allows for easy testing, maintenance, and scalability. The separation of concerns and the modularity of the layers make it easier to develop and maintain complex software systems, and adapt to changing business requirements and technical details.

-----------------------------------------------------------------------------------
</br>

### Q-What is DDD? (Domain-Driven Design)
DDD stands for Domain-Driven Design, which is an approach to software development that focuses on designing software based on the business domain and its requirements. The main goal of DDD is to create software that reflects the business domain as closely as possible, and to make it easier to understand and maintain.

The key principles of DDD include:

Ubiquitous Language: DDD emphasizes the importance of establishing a common language between developers and business stakeholders that accurately reflects the business domain. This helps to ensure that the software reflects the business requirements and is easier to understand and maintain.

Bounded Contexts: DDD defines Bounded Contexts as a way of dividing a large, complex system into smaller, more manageable pieces. Each Bounded Context has its own language, models, and rules that reflect the specific requirements of that part of the system.

Aggregates: DDD defines Aggregates as a way of grouping related entities and value objects together into a single unit of consistency. Aggregates are used to enforce business rules and ensure that the data is consistent and valid.

Entities and Value Objects: DDD distinguishes between Entities, which have a unique identity and can change over time, and Value Objects, which represent a specific value or concept and are immutable.

Domain Events: DDD emphasizes the use of Domain Events as a way of capturing and responding to changes in the system. Domain Events are used to trigger actions and update other parts of the system in response to changes in the domain.

DDD also places a strong emphasis on collaboration between developers and business stakeholders, with the goal of creating software that accurately reflects the business domain and its requirements.

In summary, DDD is an approach to software development that focuses on designing software based on the business domain and its requirements. By emphasizing a common language, Bounded Contexts, Aggregates, Entities and Value Objects, Domain Events, and collaboration between developers and business stakeholders, DDD helps to create software that is easier to understand, maintain, and modify over time.

--------------------------------------------------------------------------------------------------------------------------
</br>

### What is Microservice Architecture?
Microservice Architecture is an architectural style that structures an application as a collection of small, independent services that can be developed, deployed, and scaled independently of one another. Each service in a microservice architecture is designed to perform a specific business function and communicates with other services using well-defined APIs or protocols.

The main principles of microservice architecture include:

Decentralized data management: Each service manages its own data and databases, reducing the need for centralized data management.

Autonomous services: Each service is developed and deployed independently of other services, and can be scaled and updated without affecting the rest of the system.

Service-oriented architecture: Services are organized around business capabilities and expose well-defined interfaces that allow other services to communicate with them.

Continuous delivery: Microservices are deployed using continuous delivery practices to ensure fast and reliable delivery of new features and updates.

Resilience and fault tolerance: Microservices are designed to be resilient and fault-tolerant, with built-in mechanisms for handling errors and failures.

The benefits of microservice architecture include improved scalability, flexibility, and maintainability of applications, as well as better alignment with business needs and faster time-to-market for new features and services.

However, microservice architecture also comes with some challenges, such as increased complexity of managing distributed systems, the need for more advanced monitoring and testing tools, and the potential for service versioning and compatibility issues.

--------------------------------------------------------------------------------------------------------------------------
</br>

###  Microservice Architecture Advanced and disadvanced?
Microservice architecture is a software development approach that involves building a system as a collection of small, independent services that communicate with each other over a network. Here are some advanced and disadvantageous aspects of the microservice architecture:

Advantages:

Scalability: Microservices can be independently deployed and scaled horizontally, allowing for better utilization of resources and improved performance.

Agility: Microservices allow for faster development and deployment cycles, enabling teams to rapidly respond to changes in customer requirements and market conditions.

Resilience: Microservices are designed to be fault-tolerant and can continue to operate even if one or more services fail.

Flexibility: Microservices can be written in different programming languages and frameworks, allowing developers to choose the most appropriate technology for each service.

Easy Maintenance: Since each microservice is isolated and independent, updates and changes can be made without affecting the entire system.

Disadvantages:

Complexity: Microservices add complexity to the architecture, which can make development, testing, and deployment more difficult.

Increased Network Latency: Microservices communicate with each other over a network, which can introduce latency and affect performance.

Operational Overhead: Managing a large number of microservices can be challenging, requiring sophisticated deployment, monitoring, and orchestration tools.

Security: With more services, there are more attack surfaces and more points of vulnerability, which can make securing a microservices architecture more challenging.

Data Consistency: With a microservices architecture, maintaining data consistency across multiple services can be challenging, especially when dealing with complex transactions that involve multiple services.

In summary, the microservices architecture provides many benefits in terms of scalability, agility, resilience, and flexibility, but it also introduces complexity, network latency, operational overhead, security, and data consistency challenges that must be carefully managed.

--------------------------------------------------------------------------------------------------------------------------
</br>

## **Software Engineer**
### Q- Principles ? 
DRY, KISS, and YAGNI are additional principles that are often used in software development to promote simplicity, maintainability, and productivity.

DRY: Don't Repeat Yourself. This principle states that every piece of knowledge or logic in a system should have a single, authoritative representation. In other words, if there are two or more pieces of code that do the same thing, then they should be refactored into a single reusable component.

KISS: Keep It Simple, Stupid. This principle states that the simplest solution is often the best one. It encourages developers to prioritize simplicity over complexity and to avoid unnecessary complications in their code.

YAGNI: You Ain't Gonna Need It. This principle states that developers should not add functionality until it is needed. In other words, developers should avoid premature optimization or adding features that are not currently needed in the system.

Overall, these principles can help developers create more maintainable, efficient, and effective software systems. By following DRY, KISS, and YAGNI, developers can reduce code complexity, avoid unnecessary work, and focus on delivering the most valuable features to the end-users.

--------------------------------------------------------------------------------------------------------------------------
</br>

### Q-Memory managment heap and stack in c#
In C#, memory is managed by the .NET Framework through a garbage collector. The garbage collector automatically frees memory that is no longer being used by an application.

In C#, there are two main types of memory allocation: stack and heap.

The stack is used for storing value types, such as integers, booleans, and enums. The stack is a LIFO (last-in, first-out) data structure that is automatically managed by the runtime. When a value type is created, it is pushed onto the stack. When the method that created the value type exits, the value type is automatically removed from the stack.

The heap is used for storing reference types, such as objects, strings, and arrays. Reference types are created on the heap, and a reference (i.e., a pointer) to the location of the object on the heap is stored on the stack. When an object is no longer being used by an application, the garbage collector will automatically free the memory used by the object.

It's important to note that the heap is much larger than the stack, and is not automatically managed by the runtime. Instead, the garbage collector periodically scans the heap to identify objects that are no longer being used, and frees the memory used by those objects.

In summary, C# uses a garbage collector to automatically manage memory, and allocates value types on the stack and reference types on the heap.

--------------------------------------------------------------------------------------------------------------------------
</br>

## **Front end**
### What is angular ? and life cycle hocks?
Angular is a popular open-source web application framework used for building complex and dynamic single-page applications. It is developed and maintained by Google and provides a complete solution for building client-side applications, including components, services, routing, and data binding.

Angular has a concept called "lifecycle hooks" that allows you to tap into certain moments in the lifecycle of a component or directive. These hooks enable you to execute your own custom code at specific points in the component or directive's life cycle.

Angular provides eight lifecycle hooks:

ngOnChanges: This hook is called whenever the input properties of a component change. It receives a SimpleChanges object that contains information about the changed properties.

ngOnInit: This hook is called after the first ngOnChanges hook and once the component is initialized. It is the perfect place to initialize data and make API calls.

ngDoCheck: This hook is called whenever Angular detects a change that is not triggered by an input property. It is used for custom change detection and optimization.

ngAfterContentInit: This hook is called after the content of a component or directive is initialized. It is used to perform operations on the content of the component.

ngAfterContentChecked: This hook is called after the content of a component or directive is checked for changes. It is used to perform operations on the content of the component.

ngAfterViewInit: This hook is called after the view of a component or directive is initialized. It is used to perform operations on the view of the component.

ngAfterViewChecked: This hook is called after the view of a component or directive is checked for changes. It is used to perform operations on the view of the component.

ngOnDestroy: This hook is called just before the component or directive is destroyed. It is used to clean up resources like event listeners, subscriptions, or timers.

Using lifecycle hooks, you can add behavior to your components or directives at specific moments in their lifecycle, giving you more control and flexibility over their behavior.

--------------------------------------------------------------------------------------------------------------------------
</br>

### What is NGRX? and what's it solved ? and state managment ? 
NGRX is a library for state management in Angular applications, which is inspired by the Redux pattern. It provides a predictable and centralized way of managing application state, making it easier to develop, test, and maintain complex applications.

State management refers to the way an application manages and updates its state or data, including user input, server responses, and other changes. As an application grows in size and complexity, managing state can become challenging, leading to bugs and errors.

NGRX solves this problem by providing a set of tools and techniques for managing application state. It introduces the concept of a "store" that holds the state of the application and can be updated using "actions". Reducers are used to process these actions and update the state in the store. Components can then subscribe to the store to receive updates when the state changes.

The benefits of using NGRX for state management include:

Centralized state management: By using a centralized store to manage application state, NGRX provides a single source of truth for the entire application.

Predictable state changes: NGRX ensures that state changes are predictable and occur in a consistent way, making it easier to debug and maintain the application.

Improved performance: By using immutable data structures, NGRX can improve performance by reducing the number of unnecessary updates.

Easy testing: NGRX provides a clear separation between state management and UI components, making it easier to test the application logic.

Scalability: NGRX is designed to work with large and complex applications, making it easier to scale the application as it grows.

In summary, NGRX is a powerful tool for managing application state in Angular applications. By providing a predictable and centralized way of managing state, NGRX can help to improve performance, maintainability, and scalability of the application.

--------------------------------------------------------------------------------------------------------------------------
</br>

### What is directive  ? 
In Angular, a directive is a special type of component that allows you to add custom behavior to an existing DOM element, attribute, or component. Directives are used to manipulate the behavior of the DOM, and they are defined using the @Directive decorator.

There are three types of directives in Angular:

Component Directive: A component directive is a special type of directive that has its own view, and it can be used as a standalone element in the application. In other words, a component is a directive with a template.

Attribute Directive: An attribute directive is a directive that modifies the behavior of an existing DOM element by adding or removing attributes. For example, the ngClass directive can be used to add or remove CSS classes from an element.

Structural Directive: A structural directive is a directive that modifies the structure of the DOM by adding or removing elements. For example, the ngFor directive can be used to repeat a set of elements based on an array.

Directives are an essential part of Angular, and they allow you to extend the HTML language with custom functionality. By using directives, you can create reusable components that can be easily shared across multiple parts of your application, making your code more modular and maintainable.

--------------------------------------------------------------------------------------------------------------------------
</br>

### What is Pipe  ? 
In Angular, a pipe is a way to transform data in a template before it is displayed to the user. Pipes are defined using the @Pipe decorator and can be used with interpolation {{}} or the ngFor directive.

Pipes allow you to format and transform data in a way that is easy to use and understand. For example, you can use the DatePipe to format a date into a specific format, or the DecimalPipe to format a number with a specific number of decimal places.

There are two types of pipes in Angular:

Pure pipes: Pure pipes are the most common type of pipe, and they are called only when the input value changes. They do not have any side effects and always return the same output for a given input.

Impure pipes: Impure pipes are called on every change detection cycle, even if the input value has not changed. They can have side effects and are not recommended for use in performance-critical scenarios.

You can also create custom pipes to perform custom transformations on data. Custom pipes can be used to encapsulate complex logic or calculations and make them easier to use and understand.

In summary, pipes are a powerful feature of Angular that allow you to transform data in a template before it is displayed to the user. By using pipes, you can format and manipulate data in a way that is easy to use and understand, making your application more flexible and maintainable.

