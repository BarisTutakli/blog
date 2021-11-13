---
layout: post
title: Coding challenge 2
subtitle: Decision making, while and doWhile 
tags: [c#]
comments: false
---

Let's learn if statement, else statement and do some coding exercices. Then, i will continue by learning and practicing "Do While".<br>
Let's start with a real world example. Consider that you have two pens, one is red and the other is black. if you pick red one, your theacher won't read your essay. What would you do? Of course, you will complete your writing by using the black pen.

```c#
Console.WriteLine("Read the rules before writing an article");
string red = "red";
string black = "black";
string yourChoice = Console.ReadLine();
if(yourChoice == red){
    Console.WriteLine("your theacher won't read your essay");
}else{
    Console.WriteLine("your theacher will read your essay");
}
```
<br>
### exercise 1

```c#
Console.WriteLine("Hello World!");

Console.Write("Number : ");
int number = Convert.ToInt32(Console.ReadLine());
bool control = number > 5;
if (kontrol == true)
{
    Console.WriteLine("The number is bigger than five.");

}
else
{
    Console.WriteLine("number is less than five");
}
```

### exercise 1

Here, i tried to get two numbers from user. Then, i write the bigger one and the smaller using Console.WriteLine();<br>
```c#
Console.Write("Enter a number :");
int num1 = Convert.ToInt32(Console.ReadLine());
Console.Write("Enter a number:");
int num2 = Convert.ToInt32(Console.ReadLine());
if(num1> num2)
{
    Console.WriteLine($"The bigger number :{num1}");
}
else if(num1 < num2)
{
    Console.WriteLine($"The smaller number :{num2}");
            }
else
{
    Console.WriteLine("They are equal.");
}

```