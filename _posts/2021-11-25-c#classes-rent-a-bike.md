---
layout: post
title: Coding Challenge 8
subtitle: C# exercises - Rent a Bike 
tags: [c#,object oriented programming, oop, constructor, encapsulation,fields, properties, Rent a bike]
comments: false
---

<p style='text-align: justify;'>
We talked about fields, properties, classes, encapsulation, getter and setter methods. Now it's time to do some exercises. Let's create a basic project named Rent a Bike.</p> 

## Rent a Bike
<p style='text-align: justify;'>
 We need a User class, a Bicycle class, a Renting class.</br> Each user should have a first name, last name and an id. User class: <b>(private int)</b>id, <b>(private string)</b>first name, <b>(private string)</b>last name, getters and setters. Each bicycle has an id, a brand name, a model, a rim and gears. Bicycle class: <b>(private int)</b>id, <b>(private string)</b>brand name, <b>(private string)</b>model, <b>(private string)</b>rim size, <b>(private int)</b>gears, getters and setters. The last class is  a renting class that has the properties following. Renting class: bicycle, userName, time, price, starting time, getters, setters, StartRenting(), EndRenting(), DebtCalculator(), ToString().</br>
<b>After explaining c# abstract classes and interfaces to you, we will develop this project again using abstract classes and interfaces.</b></p>



<p style='text-align: justify;'>
Do not forget to read the comments inside the code blocks!</p> 

#### Program.cs

```c#
class Program {
    static void Main(string[] args)
    {

        User user1 = new User("Bob","Marley","5555555");
        User user2 = new User("George", "Alsion", "666666");
        User user3 = new User("Michelle", "Larison", "7777777");
        Bicycle bicycle = new Bicycle("MBI", "sport", "18", 21);
        Bicycle bicycle2 = new Bicycle("F1", "Race", "41", 28);
        Bicycle bicycle3 = new Bicycle("Toyota", "retro", "18", 8);

        Renting rent1 = new Renting(user1, bicycle);
        rent1.StartRenting();
        Thread.Sleep(5000);
        rent1.EndRenting();
        Console.WriteLine(rent1.ToString());

        Renting rent2 = new Renting(user1, bicycle);
        rent2.StartRenting();
        Thread.Sleep(7000);
        rent2.EndRenting();
        Console.WriteLine(rent2.ToString());

        Renting rent3 = new Renting(user1, bicycle);
        rent2.StartRenting();
        Thread.Sleep(3000);
        rent3.EndRenting();
        Console.WriteLine(rent3.ToString());


    }
}

```

####  User Class

```c#
class User {
    // We count the number of users and give them a unique id.
    static int count = 0; 
    private int _id = 0;
    private string _firstName;
    private string _lastName;
    private string _tel;


    // This is a constructor. 
    public User(string firstName, string lastName, string tel)
    {
        count += 1;
        this._id += count;
        this._firstName = firstName;
        this._lastName = lastName;
        this._tel = tel;
    }

    public int Id { get => _id; }

    // If the value is not null or empty and is not null or white space,  we change _firstName.
    public string FirstName
    {
        get => _firstName; set
        {
            if (!string.IsNullOrEmpty(value) && (!String.IsNullOrWhiteSpace(value)))
            {
                _firstName = value;
            }
        }
    }


    public string LastName { get => _lastName; set
        {
            if (!string.IsNullOrEmpty(value) && (!String.IsNullOrWhiteSpace(value)))
            {
                _lastName = value;
            }
        }}


    public string Tel { get => _tel; set {
            if (!string.IsNullOrEmpty(value) && (!String.IsNullOrWhiteSpace(value)))
            {
                _tel = value;
            }
        } }

}

```

####  Bicycle Class

```c#
class Bicycle {
    
    static int bicycleCount = 0;
    private int _id = 0;
    private string _brand;
    private string _model;
    private string _rimSize;
    private int _numberOfGears;


    public Bicycle(string brand, string model, string rimSize, int numberOfGears)
    {
        bicycleCount = +1;
        _id = bicycleCount;
        Brand = brand;
        Model = model;
        RimSize = rimSize;
        NumberOfGears = numberOfGears;
    }


    public string Brand { get => _brand; set => _brand = value; }
    public string Model { get => _model; set => _model = value; }
    public string RimSize { get => _rimSize; set => _rimSize = value; }
    public int NumberOfGears { get => _numberOfGears; set => _numberOfGears = value; }

}

```

####  Renting Class

```c#
class Renting {
    static int totalRentedBicycle = 0;
    private int _id;
    private User _user;
    private Bicycle _bicycle;
    private TimeSpan _usedTime;
    private double _charge =0;
    private DateTime _start;
    private DateTime _finish;

    public Renting( User user, Bicycle bicycle)
    {
        totalRentedBicycle += 1;
        this._id = totalRentedBicycle;
        this._user = user;
        this._bicycle = bicycle;
    }

    public void StartRenting()
    {
        this._start = DateTime.Now;
        
    }
    public void EndRenting()
    {
        this._finish = DateTime.Now;
    }

    public double DebtCalculator()
    {

        TimeSpan diff = _finish - _start;
        return diff.Seconds * 0.5;
    }

    public override string ToString()
    {
        return $"Started at: {this._start}\nFinished at:{this._finish}\n Debt: {DebtCalculator()}";
    }

}
```

