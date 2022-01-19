---
layout: post
title: Coding Challenge 16
subtitle: .NET Bootcamp Research Notes
tags: [C#, .NET, C# Attributes and Reflection, Attributes, Reflection]
comments: false
---

<p style='text-align: justify;'>
In this tutorial, we are going to learn C# Attributes, C# Reflection, C# Type,<br>
</p>

#### C# Attributes and Reflection

<p style='text-align: justify;'>
An attribute is an abstract class that can be used to get more information about classes, methods, parameters, etc. at runtime using Reflection. I do not want to bother you with definitions. Let's start by analyzing a simple class. Then we will discover information about System.Attribute, System.Type, System.String using reflection. You can find all the information in the output generated when I run the code.</p>

##### Calculator.cs

```c#

 public class Calculator
    {
        public int MyProperty { get; set; }
        public Calculator()
        {
            Console.WriteLine("I'm a calculator");
        }

        public int Square(int number) =>  number*number;
        public int Cube(int number) => number * number * number;
        public void Print() => Console.WriteLine("What are you doing?");

    }

```
##### Program.cs
```c#

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Let's analyse Calculator  class\n");
        Type calculator = typeof(Calculator);

        string MethodInfoResult = "";
        foreach (MethodInfo item in calculator.GetRuntimeMethods())
        {
            MethodInfoResult += $"Name: {item.Name}";
            MethodInfoResult += $"\nIsPublic: {item.IsPublic}\n----- parameters-----";
            if (item.GetParameters().Length>0&& item.ReturnParameter!=null)
            {
                foreach (var param in item.GetParameters())
                {
                    
                    MethodInfoResult += $"\nParameter: {param}\tParameterType: {param.ParameterType}";
                    MethodInfoResult += $"\nReturnType: {item.ReturnType}\tReturnValue:{item.ReturnParameter}";
                    
                }
            }
            else
            {
                MethodInfoResult += "\nParameters not found";
                MethodInfoResult += $"\nThis is a public method: {item.IsPublic}";
                
            }
            
            MethodInfoResult += "\n----------------------------------------\n";
        }
        MethodInfoResult += $"\n--------Fields-----";

        foreach (var fields in calculator.GetFields())
        {
            MethodInfoResult += $"\nPropertyName: {fields.Name}\tPropertyType: {fields.FieldType}";
        
        }
        
        Console.WriteLine(MethodInfoResult);        

    }
}

```

Output:

```c#
This is a public method: True
----------------------------------------
Name: set_ThisIsAProperty
IsPublic: True
----- parameters-----
Parameter: Int32 value  ParameterType: System.Int32
ReturnType: System.Void ReturnValue:Void
----------------------------------------
Name: Square
IsPublic: True
----- parameters-----
Parameter: Int32 number ParameterType: System.Int32
ReturnType: System.Int32        ReturnValue:Int32
----------------------------------------
Name: Cube
IsPublic: True
----- parameters-----
Parameter: Int32 number ParameterType: System.Int32
ReturnType: System.Int32        ReturnValue:Int32
----------------------------------------
Name: Print
IsPublic: True
----- parameters-----
Parameters not found
This is a public method: True
----------------------------------------
Name: GetType
IsPublic: True
----- parameters-----
Parameters not found
This is a public method: True
----------------------------------------
Name: MemberwiseClone
IsPublic: False
----- parameters-----
Parameters not found
This is a public method: False
----------------------------------------
Name: Finalize
IsPublic: False
----- parameters-----
Parameters not found
This is a public method: False
----------------------------------------
Name: ToString
IsPublic: True
----- parameters-----
Parameters not found
This is a public method: True
----------------------------------------
Name: Equals
IsPublic: True
----- parameters-----
Parameter: System.Object obj    ParameterType: System.Object
ReturnType: System.Boolean      ReturnValue:Boolean
----------------------------------------
Name: GetHashCode
IsPublic: True
----- parameters-----
Parameters not found
This is a public method: True
----------------------------------------

--------Fields-----
PropertyName: ThisIsAField      PropertyType: System.String
....
```



##### System.Attribute

```c#
class Program
{
    static void Main(string[] args)
    {
            Console.WriteLine("Let's analyse Attribute abstract class under System.Reflection class\n");
            Type obj = typeof(Attribute);

            string MethodInfoResult = "";
            foreach (MethodInfo item in obj.GetRuntimeMethods())
            {
                MethodInfoResult += $"Name:{item.Name}\tNumberofParameters: {item.GetParameters().Length}\tReturnType: {item.ReturnType}\n" +
                $"DeclaringType: {item.DeclaringType}\tIsPrivate: {item.IsPrivate}\tIsPublic: {item.IsPublic}\n" +
                $"Type: {item.GetType().GetTypeInfo()}";
                if (item.GetParameters().Length > 0)
                {
                    string itemParams = "";
                    foreach (var param in item.GetParameters())
                    {
                        itemParams += $"\nParam: {param}\tParamType: {param.ParameterType}";

                    }
                    MethodInfoResult += itemParams;
                }
                MethodInfoResult += "\n----------------------------------------\n";
            }
            Console.WriteLine(MethodInfoResult);

    }
}
```
Output:

```c#
Let's analyse Attribute abstract class under System.Reflection class

Name:InternalGetCustomAttributes        NumberofParameters: 3   ReturnType: System.Attribute[]
DeclaringType: System.Attribute IsPrivate: True IsPublic: False
Type: System.Reflection.RuntimeMethodInfo
Param: System.Reflection.PropertyInfo element   ParamType: System.Reflection.PropertyInfo
Param: System.Type type ParamType: System.Type
Param: Boolean inherit  ParamType: System.Boolean
----------------------------------------
Name:InternalIsDefined  NumberofParameters: 3   ReturnType: System.Boolean
DeclaringType: System.Attribute IsPrivate: True IsPublic: False
Type: System.Reflection.RuntimeMethodInfo
Param: System.Reflection.PropertyInfo element   ParamType: System.Reflection.PropertyInfo
Param: System.Type attributeType        ParamType: System.Type
Param: Boolean inherit  ParamType: System.Boolean
----------------------------------------
Name:GetParentDefinition        NumberofParameters: 2   ReturnType: System.Reflection.PropertyInfo
DeclaringType: System.Attribute IsPrivate: True IsPublic: False
Type: System.Reflection.RuntimeMethodInfo
Param: System.Reflection.PropertyInfo property  ParamType: System.Reflection.PropertyInfo
Param: System.Type[] propertyParameters ParamType: System.Type[]
----------------------------------------
Name:InternalGetCustomAttributes        NumberofParameters: 3   ReturnType: System.Attribute[]
DeclaringType: System.Attribute IsPrivate: True IsPublic: False
Type: System.Reflection.RuntimeMethodInfo
Param: System.Reflection.EventInfo element      ParamType: System.Reflection.EventInfo
Param: System.Type type ParamType: System.Type
Param: Boolean inherit  ParamType: System.Boolean
----------------------------------------
Name:GetParentDefinition        NumberofParameters: 1   ReturnType: System.Reflection.EventInfo
DeclaringType: System.Attribute IsPrivate: True IsPublic: False
Type: System.Reflection.RuntimeMethodInfo
Param: System.Reflection.EventInfo ev   ParamType: System.Reflection.EventInfo
....
```

---------------------------type-----------------------

```c#
class Program
{
    static void Main(string[] args)
    {
            Console.WriteLine("Let's analyse System.Type derived from IReflect and MemberInfo  class\n");
            Type obj = typeof(Type);

            string MethodInfoResult = "";
            foreach (MethodInfo item in obj.GetRuntimeMethods())
            {
                MethodInfoResult += $"Name:{item.Name}\tNumberofParameters: {item.GetParameters().Length}\tReturnType: {item.ReturnType}\n" +
                $"DeclaringType: {item.DeclaringType}\tIsPrivate: {item.IsPrivate}\tIsPublic: {item.IsPublic}\n" +
                $"Type: {item.GetType().GetTypeInfo()}";
                if (item.GetParameters().Length > 0)
                {
                    string itemParams = "";
                    foreach (var param in item.GetParameters())
                    {
                        itemParams += $"\nParam: {param}\tParamType: {param.ParameterType}";

                    }
                    MethodInfoResult += itemParams;
                }
                MethodInfoResult += "\n----------------------------------------\n";
            }
            Console.WriteLine(MethodInfoResult);

    }
}
```


<p style='text-align: justify;'>
If you read this post, probably you are familiar with System.String. Now, let's discover it again using reflection. </p>

##### Program.cs
```c#
class Program
{
    static void Main(string[] args)
    {

        Console.WriteLine("Let's analyse System.String class\n");
        Type obj = typeof(String);
        string MethodInfoResult = "";
        foreach (MethodInfo item in obj.GetRuntimeMethods())
        {
            MethodInfoResult += $"Name:{item.Name}\tNumberofParameters: {item.GetParameters().Length}\tReturnType: {item.ReturnType}\n" +
            $"DeclaringType: {item.DeclaringType}\tIsPrivate: {item.IsPrivate}\tIsPublic: {item.IsPublic}\n" +
            $"Type: {item.GetType().GetTypeInfo()}";
            if (item.GetParameters().Length > 0)
            {
                string itemParams = "";
                foreach (var param in item.GetParameters())
                {
                    itemParams += $"\nParam: {param}\tParamType: {param.ParameterType}";

                }
                MethodInfoResult += itemParams;
            }
            MethodInfoResult += "\n----------------------------------------\n";
        }
        Console.WriteLine(MethodInfoResult);
    }
}
```
Output:

```c#
Let's analyse System.String class
Name:Replace    NumberofParameters: 4   ReturnType: System.String
DeclaringType: System.String    IsPrivate: False        IsPublic: True
Type: System.Reflection.RuntimeMethodInfo
Param: System.String oldValue   ParamType: System.String
Param: System.String newValue   ParamType: System.String
Param: Boolean ignoreCase       ParamType: System.Boolean
Param: System.Globalization.CultureInfo culture ParamType: System.Globalization.CultureInfo
----------------------------------------
Name:Replace    NumberofParameters: 3   ReturnType: System.String
DeclaringType: System.String    IsPrivate: False        IsPublic: True
Type: System.Reflection.RuntimeMethodInfo
Param: System.String oldValue   ParamType: System.String
Param: System.String newValue   ParamType: System.String
Param: System.StringComparison comparisonType   ParamType: System.StringComparison
----------------------------------------
Name:ReplaceCore        NumberofParameters: 4   ReturnType: System.String
DeclaringType: System.String    IsPrivate: True IsPublic: False
Type: System.Reflection.RuntimeMethodInfo
Param: System.String oldValue   ParamType: System.String
Param: System.String newValue   ParamType: System.String
Param: System.Globalization.CompareInfo ci      ParamType: System.Globalization.CompareInfo
Param: System.Globalization.CompareOptions options      ParamType: System.Globalization.CompareOptions
....
```


[Reflection&Attributes](https://www.c-sharpcorner.com/uploadfile/ashish_2008/reflection-and-attributes-in-C-Sharp/)

[Attributes](https://www.pluralsight.com/guides/using-attributes-in-c)
