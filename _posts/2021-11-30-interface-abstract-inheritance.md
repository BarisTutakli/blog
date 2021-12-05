---
layout: post
title: Coding Challenge 9
subtitle: C# İnterface, Abstraction, Inheritance and Polymorphism
tags: [c#,object oriented programming, oop, constructor, İnterface, Abstract, İnheritance, Polymorphism]
comments: false
---

<p style='text-align: justify;'>
Why should use interfaces? How to define interfaces? how could a class inherit from another class? What is an abstract class? When ı start learning inheritance, interfaces, abstract classes, i google it a lot. However, i saw that many sites use similiar examples. They are using either car class or animal class to explain inheritance and interfaces or abstract classes. Using them in different projects does not show how to use them in one project. This situation made me confused. So, i will do my best to clear your mind using different exercises.</p>

## C# Inheritance

<p style='text-align: justify;'>
Let's continue with a real world example! Suppose that you are creating a program that meets the needs of a bank. If you create  Worker class and Manager class, you will repeat some codes because they have some commons properties. So, we create a class named Person that contains common features. Worker class and Manager class will inherit features of Person class. Create Person.cs, Worker.cs and Manager.cs, then see what happens in program.cs </p>

#### Person.cs

```c#
class Person {

    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Email { get; set; }
    public Person(string firstName, string lastName, string email)
    {
        FirstName = firstName;
        LastName = lastName;
        Email = email;
    }

    public void WhoAmI()
    {
        Console.WriteLine($"I am a person and my name is {this.FirstName}");
    }
```
#### Worker.cs

```c#
class Worker:Person {
    public string Mission { get; set; }
    public Worker(string firstName, string lastName, string email, string mission ) : base(firstName, lastName, email)
    {
        Mission = mission;
    }
    public void WhoAmI()
    {
        base.WhoAmI();
        Console.WriteLine($"{this.FirstName} is also a worker");
    }

}

```

#### Manager.cs

```c#
class Manager: Person {
    public List<string> Teams { get; set; }
    public Manager(string firstName, string lastName, string email, List<string> teams) : base(firstName, lastName, email)
    {
        Teams = teams;
    }
    public void WhoAmI()
    {
        base.WhoAmI();
        Console.WriteLine($"{this.FirstName} is also a manager");
    }

}
```
<p style='text-align: justify;'>
In program.cs we will create an instance of Person class an isntance of Worker class and an isntance of Manager class.  We did not declare FirstName, Lastname, Email in Worker.cs and Manager.cs; but we used all of them because Worker.cs and Manager.cs inherit from Person class using <b>Worker: Person</b> and <b>Manager: Person</b>. To sum up, inheritance reduced code size</p>

```c#
class Program {
    static void Main(string[] args)
    {
        Person person = new Person("Bob","Marley","bobmarley@hotmail.com");
        Worker worker = new Worker("Dennis","Ka","deniska@hotmail.com","Cleaning");
        Manager manager = new Manager("Steve", "Jobs", "stevejobs@hotmail.com",new List<string>{ "It","HR"} );

        person.WhoAmI();
        worker.WhoAmI();
        manager.WhoAmI();
    }

}
```

Output:<br>
I am a person and my name is Bob<br>
I am a person and my name is Dennis<br>
Dennis is also a worker<br>
I am a person and my name is Steve<br>
Steve is also a manager<br>
 
## C# Abstraction
<p style='text-align: justify;'>
Abstraction can be made by abstract classes or interfaces. The important thing is that you can not create an instance of them. To use an abstract class, another class should inherit it. If you declare an abstract class with the keyword sealed, it cannot be inherited. To clear up, i'm gonna try to explain it in a different way.
Consider that there are a man and a woman who can not be able to have a child because the man has health problems. However they want to give birth a baby that's why they found a sperm donor to get her pregnant. Now, there are an abstract father(abstract class) of the baby and one real mother(base class) and her husband(interface). The child inherits some properties from the donnor and her mother. As the baby grows, he/she imitates her mother and father. Here we see that child's behavior changes(the intent of abstract method change in the child class). They educate the child the way they want. Now let's create these classes.</p>

```c#
abstract class Donnor
{
  // This is an Abstract method
  public abstract void Learn();
  // Regular method
  public void Cry()
  {
    Console.WriteLine("*_*");
  }
}

```
<p style='text-align: justify;'> <b>Derived class (inherits from Animal)</b></p>

```c#
class Baby : Donnor, Father
{
  public override void Learn()
  {
    //the code block of abstract method
    Console.WriteLine("I want to learn play piano like my father:)");
  }
}
```
#### Program.cs

```c#
class Program
{
  static void Main(string[] args)
  {
    Baby myBaby = new Baby(); // Give birth a baby.
    myBaby.Learn();  // Call the abstract method
    myBaby.Cry();  // Call the regular method
  }
}

```

## C# interface

<p style='text-align: justify;'>
An interface contains only abstract methods and properties. To recognize an interface, people start with the letter "I" at the beginning of an interface name. There ia an obvious difference between an abstract class and an interface. A class can inherit many interfaces, but not more than one abstract class. I created three interfaces below.</p>

#### ISpeak, IRun and IEat

```c#
interface ISpeak 
{
  void Speaking(); 
}
interface IRun 
{
  void Running(); // interface method
}
interface IEat 
{
  void Eating(); // interface method
}
```

#### Test
Test Class inherits ISpeak, IRun and IEat. 

```c#
class  Test : ISpeak, IRun, IEat 
{
  public void Speaking() 
  {
    Console.WriteLine("I'm speaking...");
  }
  public void Running() 
  {
    Console.WriteLine("I'm running..");
  }
    public void Eating() 
  {
    Console.WriteLine("I'm eating...");
  }

}
```

#### Program.cs

```c#
class Program 
{
  static void Main(string[] args)
  {
    Test test = new Test();
    test.Speaking();
    test.Running();
    test.Eating();
  }
}
```

See you in my next post:)