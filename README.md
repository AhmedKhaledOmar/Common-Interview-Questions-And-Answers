# Common-Interview-Questions-And-Answers
## **Design patterns:**
### 1- What's Design Pattern?
A design pattern is a general reusable solution to a commonly occurring problem within a particular context in software design. It is a description or template for how to solve a particular problem that can be adapted and reused in different situations. Design patterns are like templates or blueprints for building software that help developers solve common problems in an efficient and effective way.

Design patterns can be categorized into three main groups: creational, structural, and behavioral. Creational patterns are concerned with object creation mechanisms, trying to create objects in a manner suitable to the situation. Structural patterns deal with object composition, forming class hierarchies, and defining how objects are composed to form larger structures. Behavioral patterns are concerned with communication between objects, encapsulating behaviors and interactions between objects.

The use of design patterns can provide several benefits, such as reducing the time and effort needed to solve common problems, improving code readability and maintainability, facilitating communication between team members, and promoting code reusability. There are many well-known design patterns, such as the Singleton pattern, Factory pattern, Observer pattern, Decorator pattern, and many more.
<small>
By understanding and applying design patterns, developers can create more robust, maintainable, and extensible software that can better meet the needs of their users. However, it's important to note that design patterns should be used judiciously and only where appropriate. Overuse or misuse of design patterns can lead to unnecessarily complex and difficult-to-maintain code.
</small>

-----------------------------------------------------------------------------------
</br>

## **OOP:**
### 1- Different between interface and abstract?
Both abstract classes and interfaces are used to define abstract types in object-oriented programming. Here are some of the main differences between them:

Implementation: An abstract class can contain some implementation code, while an interface cannot. Abstract classes can provide default implementations for some or all of their methods, which can be overridden by subclasses. Interfaces, on the other hand, do not contain any implementation code at all.

Multiple inheritance: A class can only inherit from one abstract class, but it can implement multiple interfaces. This is because an abstract class is a type of class, while an interface is a separate construct that can be implemented by any class.

Accessibility: Methods and fields of an interface are by default public, while an abstract class can have different access modifiers for its methods and fields.

Purpose: Abstract classes are used to define a base class for a group of related classes, while interfaces are used to define a contract that a class must follow.

Constructors: An abstract class can have a constructor, while an interface cannot.

In general, abstract classes are used when you want to create a common base class for a group of related classes, and when you want to provide some default implementation code for those classes. Interfaces, on the other hand, are used when you want to define a contract that a class must follow, but you don't care about its implementation.

It's also worth noting that in some programming languages, such as C#, interfaces can contain default implementations for their methods using default interface methods. This blurs the distinction between interfaces and abstract classes somewhat, but the basic differences outlined above still hold.

**Note** : In last version in C# Interface can contain some implementation.

-----------------------------------------------------------------------------------
### 2- Difference between overloading and override?
<small>
Overloading is the ability to define two or more methods with the same name in a single class, but with different parameters. This allows you to provide multiple methods with different behaviors, but with the same name, making it easier to call them. Overloading allows you to create methods that have the same name but perform different tasks, based on the parameters that are passed to them. The methods can have different access modifiers, return types, and/or number of parameters. Overloading is resolved at compile time, based on the number and types of the arguments provided.
</small>

-----------------------------------------------------------------------------------
### 3- What is delegate and experssion in C# and how to use it with example ?
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

-----------------------------------------------------------------------------------
</br>

## **General Questions:**
### 1- Different between Pass by refrence and pass by value?
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
### 2- When equal refrence object to refrence object and same in case value?
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
### 3- What is Casting and type of casting in C#?
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
### 4- object obj = null; 
### - int d = (int)obj;
### - int d = obj as int ;
### - int d = Int64.Parse(obj);
### - int d = Int64.TryParse(obj)
### - int d = obj is int ;
### What happend in all this cases ?
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
</br>

## Database 
### 1- What is isolations levels?
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

## Software Architecture

### 1-What is DDD? (Domain-Driven Design)
DDD stands for Domain-Driven Design, which is an approach to software development that emphasizes the importance of understanding the domain or business problem that the software is meant to solve. DDD is based on the idea that the domain is the most important part of a software system, and that the design of the system should be driven by the domain.

DDD provides a set of principles and patterns that can help developers to create software that is more closely aligned with the business problem it is meant to solve. 

One of the key benefits of DDD is that it can help to create a shared understanding of the domain between business stakeholders and technical team members. This shared understanding can help to reduce the risk of miscommunication and ensure that the software system meets the needs of the business.

DDD is not a specific technology or tool, but rather a set of principles and practices that can be applied to any software development project. However, there are tools and frameworks available that can help to implement DDD concepts in practice, such as event sourcing, CQRS, and domain-specific languages.