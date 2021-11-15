---
layout: post
title: Coding challenge 3
subtitle: Learning and practicing c# for loop, the foreach Loop, Arrays, Multidimensional Array 
tags: [c#,Array,MultidimensionalArray, loops, for loop, foreach]
comments: false
---

Suppose that you need to create a collection of variables of the same type that's why you need an array. Arrays help you to store multiple values in a single variable. In my recent post, i shared with you ...making, while, doWhile. In this section, we will learn about arrays after learning for loop and for each loop.



## For Loop
A for loop is similar to while loop but there is a difference. To use a for loop, you need to execute a specific number of times.
### Exercise 1
```c#
for (int i = 0; i < 10; i++)
{
    Console.WriteLine($"Num: {i}");
}
```
When you run this code, you will see the numbers from one to ten on the console in order.
### Exercise 2
Write all the even numbers from one to an other number entered by an user.
```c#
int num = Convert.ToInt32(Console.ReadLine());
for (int i = 0; i < num; i++)
{
    if (i%2 ==0)
    {
        Console.WriteLine(i);
    }
}
```

## Infinite for loop 
```c#
 for (; ; )
{
    Console.WriteLine("This is an infitine loop.");

}
```
### Exercise 1

In this code, we get inputs from a user until he/she press "q".Then, we sum the negative numbers and positive numbers separately.
```c#

int negSum = 0;
int posSum = 0;
for (; ;)
{
    Console.WriteLine("Enter a number");
    string value = Console.ReadLine();
    if (value.ToLower()=="q")
    {
        Console.WriteLine("negatif:" + negSum);
        Console.WriteLine("positive:" + posSum);
        break;
    }else if(value == "34" || value == "-34")
    {
        Console.WriteLine("You entered an unvalid number");
        continue;
    }
    else
    {
        int intNum = Convert.ToInt32(value);
        if (intNum < 0)
        {
            negSum += intNum;

        }
        else if (intNum > 0)
        {
            posSum += intNum;

        }
    }
}
```
## Foreach Loop
Let's you to loop through elements in an array. In the next section, you will see how to use it.
```c#
foreach (var item in collection)
	{

	}
```

## Arrays
What does array mean? Let's discover it together! An array is just a collection of elements of the same type. 

```c#
// type[] arr = new type[10]
// type[] arr = {element1,element2,element3}
```
// To create an array with 10 ints
```c#
int[] numberArray = new int[10];
int[] numbersArray = {1,2,3,4,5,6,7,8,9}; // This is an other way to do the same thing but there is not any number in the numbers array because we didn't added any int into it.
```
// To create an array of strings
```c#
string[] strArray = new string[10];
string[] strArray = {"1asd","2asd","3asd","4asd","5asd","6asd","7asd","8asd","9asd"};
```

// To create an array of doubles

```c#
double[] doubleArray = new double[10];
double[] doubleArray = {1,2,3,4,5,6,7,8,9};
```
// To access an elements

```c#
int[] numbersArray = {1,2,3,4,5,6,7,8,9}; 
Console.WriteLine(numbersArray[3])
```
// To create an array of different type objects
```c#
object[] mixedArray = new object[10]; 
mixedArray[0] = 5;
mixedArray[2] = "string";
mixedArray[3]= 14.5f;
Console.WriteLine(mixedArray[2]);
```

In the code below, i tried to print all elements of numbersArray
```c#
int[] numbersArray = {1,2,3,4,5,6,7,8,9}; 
for (int i = 0; i < 10; i++)
{
    Console.WriteLine(numbersArray[i])
}
```
### Exercise 1
Write the code that ask a user to enter names, push them into array and print 
```c#
string[] names = new string[10];
for (int i = 0; i < 10; i++)
{
    string name = Console.ReadLine();
    names[i] = name;

}

for (int i = 0; i < names.Length; i++)
{
    Console.WriteLine(names[i]);
}
```



### Exercise 2
Generating 10 numbers randomly, adding them into array and printing all the elements of this array. 

```c#
int[] arr = new int[10];
Random randomNum;
for (int i = 0; i < 10; i++)
{
    randomNum = new Random();
    arr[i] =  randomNum.Next(0,100);
}
foreach (var item in arr)
{
    Console.WriteLine(item);
}
```
It's possible to know how many times an element is repeated in the array.

### Exercise 3

```c#
int[] numbers = { 10, 20, 30, 40, 10, 14, 10, 20, 30 };
int count10 =puanlar.Count(sayi=> sayi == 10)
Console.WriteLine($"{count10} is repeated 10 times in the array 10");
```
If you want to learn the index of this repeatitions, you can use **Array.indexOf()**

### Exercise 4
```c#
int[] numbers = { 10, 20, 30, 40, 10, 14, 10, 20, 30 };
int count10 =puanlar.Count(sayi=> sayi == 10)
int startİndex = 0;

for (int i = 0; i < count10; i++)
{
    startIndex = Array.IndexOf(numbers, 10, startIndex);
    Console.WriteLine($"The index of {count10}");
    startIndex += 1;
}
```

**when Array.indexOf() couldn't find the element in the array, it returns -1**<br>

How to Copy an array and copy one part of an array?<br>
```c#
int[] arr1 = { 11, 20, 45, 55, 66, 48, 20, 30, 40};
int[] arr2  =  new int[9];
arr1.CopyTo(arr2,0);

// Array.Copy() starts copying 5 items from 3td elements into arr2 at index 0 
Array.Copy(arr1, 3, arr2, 0, 5);

```
## Multidimensional Arrays

Let's create two dimensional array which contains 5 row and 5 columns.<br>
```c#
int[,] matrix = new int[5, 5];
marrix[0,0] = 10 // Addin 10 at (0,0)
marrix[0,0] = 100 // Addin 100 at (1,0)
marrix[0,0] = 12 // Addin 12 at (0,1)
```

### Exercise 5
 
 2 0 0 0 2<br>
 1 0 0 0 1<br>
 2 0 0 0 2<br>
 1 0 0 0 1<br>
 2 0 0 0 2<br>

```c#
for (int i = 0; i < 5; i++)
{
    for (int j = 0; j < 5; j++)
    {
        if (i % 2 == 0 &&(j==0 || j==4))
        {
            matris2[i, j] = 2;
           
        }
        else if (i % 2 == 1 && (j == 0 || j == 4))
        {
            matris2[i, j] = 1;
        }
    }
}

for (int i = 0; i < 5; i++)
{
    for (int j = 0; j < 5; j++)
    {
        Console.Write(matris2[i, j]+" ");
       }
       Console.Write("\n");
}
```