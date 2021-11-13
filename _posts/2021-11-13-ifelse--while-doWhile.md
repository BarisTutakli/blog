---
layout: post
title: Coding challenge 2
subtitle: Decision making, while and doWhile 
tags: [c#]
comments: false
---

Let's learn if statement, else statement and do some coding exercises. Then, i will continue by learning and practicing "Do While".<br>
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
### Exercise 1

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

### Exercise 2

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

### Exercise 3
Write a program that adds and prints the three numbers less than 100 entered from the keyboard.
In this section, ı ask user to enter three numbers. then, if the numbers is less than 100, ı add and print them. <br>

```c#
int sum = 0;
for (int i = 0; i < 3; i++)
{
    Console.Write($"Enter the number {i+1} : ");
    int num = Convert.ToInt32(Console.ReadLine());
    if (num<100)
    {
        sum += num;
    }
}
Console.WriteLine($"Toplam : {sum}");
```

### Exercise 4

Now, let's convert notes to letter grade. <br>
| Percent Grade | Letter | 
| :------ |:--- |
| 0-49 | F |
| 50-64 | D |
| 65-69 | C |
| 70-84 | B |
| 85-100 | A |
        
```c#

Console.Write("Enter your grade : ");
            int grade = Convert.ToInt32(Console.ReadLine());
            if (0 < grade && grade< 49)
            {
                Console.WriteLine($"You get : F");
            }
            else if (50 < grade && grade < 64)
            {
                Console.WriteLine($"You get : D");
            }
            else if (65 < grade && grade < 69)
            {
                Console.WriteLine($"You get : C");
            }
            else if (70 < grade && grade < 84)
            {
                Console.WriteLine($"You get : B");
            }
            else if (85 < grade && grade < 100)
            {
                Console.WriteLine($"You get : A");
            }
            else
            {
                Console.WriteLine($"Please, be carefu!");
            }
```

### Exercise 4

Firstly, user enter two numbers and one request. After checking inputs, if everything is valid, i print them.<br> 

```c#
Console.Write("Enter the first number  : ");
float s1 = Convert.ToSingle(Console.ReadLine());
Console.Write("Enter the second number : ");
float s2 = Convert.ToSingle(Console.ReadLine());
Console.Write("Enter (+, -, /, *): ");
string request = Console.ReadLine();
string result = "";


if(request == "+")
{
    result = Convert.ToString(s1 + s2);
    Console.WriteLine($"Result :{result} ");
}
else if (request == "-")
{
    result = Convert.ToString(s1 - s2);
    Console.WriteLine($"Result :{result} ");
}
else if (request == "/")
{
    if (s2 != 0)
    {
        result = Convert.ToString(s1 / s2);
        Console.WriteLine($"Result :{result} ");
    }
    else
    {
        Console.WriteLine("Zero division Error! ");
    }
    
    
}
else if (request == "*")
{
    result = Convert.ToString(s1 * s2);
    Console.WriteLine($"Result :{result} ");
}
else
{
    Console.WriteLine("Enter again!");
}
```
### Exercise 5
Here, the code counts the sign of the positive numbers and the negetive numbers. Then, It add them seperatly. 
 ```c#
int negativeSum = 0;
int positiveSum = 0;
int numberOfNegatives = 0;
int numberOfPositives = 0;

for (int i = 0; i < 5; i++)
{
    int num = Convert.ToInt32(Console.ReadLine());
    if (num>0)
    {
        numberOfPositives += 1;
        positiveSum += num;
    }
    else if (num<0)
    {
        numberOfNegatives += 1;
        negativeSum += num;

    }

}
Console.WriteLine($"The number of positives: {numberOfPositives}\t Sum : {positiveSum}\n" +
    $"The number of negatives: {numberOfNegatives}\t Sum : {negativeSum} ");

 ```

 ## while loop
 To use while loop, we specify a condition, the block of code will continue to run again and again until the condition is met.

```c#
while (condition)
	{

	}
```

### Exercise 1
Let's trying to print numbers from 1 to 10.

```c#
byte num = 1;
while (num<= 10 )// loop will execute this block untill number = 10
{
    Console.WriteLine(num);
    num ++;
}
```

### Exercise 2

The code will continue to run until the moment that user enters "q". During this process, the code sums the entered values. In all steps, we see the result.  <br>

```c#
string input = Console.ReadLine();
int sum = 0;
bool isParsable = Int32.TryParse(input, out _);
while (input != "q")
{
    if(isParsable == true)
    {
        sum += int.Parse(input);
                    
    }
    else
    {
        Console.WriteLine("You entered incorrectly!");
               
                  

    }
    Console.Write("Enter a number again: ");
    input = Console.ReadLine();
    isParsable = Int32.TryParse(input, out _);



}
Console.WriteLine($"Sum of inputs: {sum} 
```
### Exercise 3
We print even and odd numbers from 1 to 100.
```c#
int count = 1;
while (count<100)
{
    if(count%2 == 0)
    {
        Console.WriteLine($"{count} is an even.");
                    
    }
    else
    {
        Console.WriteLine($"{count} is a odd.");
    }
    count++;
}
```

#### break
If you read up to now, it's almost over. "break" helps you to stop a loop. Let's make an example.

### Exercise 4
The loop will continue till you enter 19 or a multiple of 19. <br>
```c#
bool check = true;
Console.Write("Enter a number :");
int num = Convert.ToInt32(Console.ReadLine());
while (check)
{

    if (num % 5 == 0)
    {
        Console.WriteLine("BOOM");
    }
    else if (num % 19 == 0)
    {
        break;
    }
    Console.Write("Enter a number:");
    num = Convert.ToInt32(Console.ReadLine());

}
```
#### continue
"While" helps you to pass one step that you don't want to run this code. Let's make an example.<br>
```c#
int i = 1;
while (i<=10)
{
    if (i==7)
    {
        i++;
        continue;// we skip 7 and continue prinint till 9
    }
    else if (i==9)

    {
        break;
    }
    Console.WriteLine(i);
    i++;

}
```c#