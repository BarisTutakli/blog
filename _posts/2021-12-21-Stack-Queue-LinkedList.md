---
layout: post
title: Coding Challenge 11
subtitle: Data Structure and algorithms
tags: [c#,Data Structure, algorithms,queue,stack, CallCenterExample,LinkedList]
comments: false
---

<p style='text-align: justify;'>
In this tutorial, we are going to discover the stack data, the queue data and LinkedList data structure. As usuall, we start learning by asking questions to deep dive into subjects. Data structure is used to store and organize data. Imagine that you want to fecth a user data from a list with more than millions of user. If you for loop throut it, it will be long enough to find the user depending on your luck:) However, users won't wait  and you will lose users. You will lose as many users as you lose money.   </p>

#### Why should i learn data structures and algorithms?
I answered this question above.

#### Are there any real world examples related to data structures?
<p style='text-align: justify;'>Yep, there are many real world examples. Let's look at the image belove and try to get the bottom ball? To get the bottom ball, we takes the other balls out. Then, we get the bottom ball. When you use the stack structure, it will behave like you did.  </p>
<<<<<<< HEAD
<img src="https://github.com/baristutakli/baristutakli.github.io/blob/master/assets/img/stack.jpg?raw=true" alt="Stack">
=======

![Stack](https://github.com/baristutakli/baristutakli.github.io/blob/master/assets/img/stack.jpg)
>>>>>>> 76f22ba145bb5457846406981e2a4e58d7e9f0b8

#### What does the stack mean?
<p style='text-align: justify;'>
In stack data structure, the first element stored will be removed last. It applies the first-in, last-out principle.</p>

#### What does the  queue mean?
<p style='text-align: justify;'>
Let's look at the image belove again and try to get the top ball? To get the top ball, we takes the top ball:) we applied the first-in, first-out principle. The queue structure do the same thing. The item that goes in first is the item that comes out first.</p>
<<<<<<< HEAD
<img src="https://github.com/baristutakli/baristutakli.github.io/blob/master/assets/img/stack.jpg?raw=true" alt="Queue">
=======

![Stack](https://github.com/baristutakli/baristutakli.github.io/blob/master/assets/img/stack.jpg)
>>>>>>> 76f22ba145bb5457846406981e2a4e58d7e9f0b8

<p style='text-align: justify;'>
For another example, let's say you go to have your car washed, the car of the person in the first line is washed first. </p>

#### What does the linkedlist mean?
<p style='text-align: justify;'>
A linkedlist is a list where each node contains a data item and a reference to the next item. To use Linkedlist, we add using System.Collections.Generic at the top of our cs fil. Let's see the stack, the queue and linkedlist in c#.</p>

#### Reverse a string using the stack
```c#
public static string ReverseString(string text)
{
    string reversed = "";
    Stack<char> stack = new Stack<char>();
    foreach (var item in text)
    {
        stack.Push(item);// First in last out
    }
    foreach (var item in stack)
    {
        reversed += item;
    }
    return rvs;
}
```
#### Reverse an int array using the stack
```c#
public static int[] ReverseArray(int[] array)
{
    List<int> reversed = new List<int>();
    Stack<int> stack = new Stack<int>();
    for (int i = 0; i < array.Length; i++)
    {
        stack.Push(array[i]);
    }
    foreach (var item in stack)
    {
        reversed.Add(item);
    }

    return reversed.ToArray();

}
```


#### program.cs 
To see the output, we called ReverseString function and ReverseArray belove.
```c#
Console.WriteLine("Original: Hello World\n"+"Reversed:" + ReverseString("Hello World"))

int[] intArray = new int[5]{ 1,2,3,4,5};
string message = "Array elements order reversed!\nOrigin :1 2 3 4 5\nNew :";

foreach (var item in LearnStack.ReverseArray(intArray))
{
    message += item+" ";
}
Console.Write(message);
```

#### Call Center System using the queue data structure
An example of a queue data structure is a call center system.
```c#
Queue<string> queue = LearnQueue.CallCenter(new List<string>() { "4441444", "5554555", "053454565" });
Console.WriteLine("Next Call:" + queue.Dequeue());
Console.WriteLine("Next Call:" + queue.Dequeue());
Console.WriteLine("Next Call:" + queue.Dequeue());
```

#### Linkedlist 

```c#
LinkedList<String> my__Linkedlist = new LinkedList<String>();
my__Linkedlist.AddLast("BMW");
my__Linkedlist.AddLast("Porche");
my_Linkedlist.AddLast("Renault");

Console.WriteLine("Car brand List:");

// Accessing the elements of 
// LinkedList Using foreach loop
foreach(string str in my_Linkedlist)
{
    Console.WriteLine(str);
}
```
