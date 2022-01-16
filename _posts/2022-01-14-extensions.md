---
layout: post
title: Coding Challenge 15
subtitle: .NET Bootcamp Research Notes
tags: [C#, .NET, Extension Method]
comments: false
---

<p style='text-align: justify;'>
In this tutorial, we are going to learn some topics such as C# extension method ...
Have you ever thought about customizing some classes? An extension method enables us to extend a class without damaging or changing the reel codes of the class that we want to modify.</p>

#### C# Extension Method

<p style='text-align: justify;'>
To create an extension method, we need to create a static class and one static method. For instance, i would like to customize C# String Class. Let's customize System.String class together and simulate Fluent Validation using C# extension method.</p>

In the code below, you can see one class called FluendValidation and three extension methods.

- IsNotNullAndNotEmpty(this string newString) returns true if an email ıs not empty and not null.
- IsNotLongEnough returns true ıf the length of a string is greater than 15.
- IsStrongEnough returns true if the password contains uppercase, lowercase, numbers, and characters.

##### FluentValidation.cs

In code block of IsStrongEnough methos, there are patterns such as @"[A-Z]", @"[a-z]", @"[0-9]" and @"\W".

- @"[A-Z]" is used to find any character from uppercase A to uppercase Z.
- @"[a-z]" is used to find any character from lowercase a to lowercase z.
- @"[0-9]" is used to find any character between 0 to 9.
- @"\W" is used to find any non-word characters.

```c#
public static class FluentValidation
{
    public static bool IsNotNullAndNotEmpty(this string newString)
    {

        return newString is not null && newString != "";
    }

    public static bool IsLongEnough(this string newString)
    {
        return newString.Length > 15 ? true:false;
    }


    public static bool IsStrongEnough(this string newString)
    {
        bool IsStrong = true;
        List<string> patterns= new List<string> { @"[A-Z]", @"[a-z]", @"[0-9]", @"\W" };
        MatchCollection regex;
        patterns.ForEach(pattern =>
        {
            regex = Regex.Matches(newString, pattern);// return a list of all matches
            if (regex.Count==0)
            {
                IsStrong = false;
            }
        }

        );

        return newString.IsLongEnough() && IsStrong ? true : false;

    }
}
```

Let's run the Program.cs file and see the results.

##### Program.cs

```c#
class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello World!");
        // How to use c# extension method
        string email= "asdfg@hotmail.com";
        string password="1234567gcyh89?AgE-";
        Console.WriteLine(email.IsNotNullAndNotEmpty());
        Console.WriteLine( password.IsNotNullAndNotEmpty());
        Console.WriteLine("IsLongEnough: " + password.IsLongEnough());
        Console.WriteLine("IsStrongEnough: " + password.IsStrongEnough());
    }
}
```

Output:

```c#
asdfg@hotmail.com is not NULL and not EMPTY: True
1234567gcyh89?AgE- is not NULL and not EMPTY: True
IsLongEnough: True
IsStrongEnough: True
```
As you see in the result, we extended System.String by adding new validation methods.