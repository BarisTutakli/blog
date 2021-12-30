---
layout: post
title: Coding Challenge 12
subtitle: Data Structure, algorithms and Hash Table
tags: [c#,Data Structure, algorithms,Hash Table]
comments: false
---
<p style='text-align: justify;'>
In this tutorial, we are going to discover the hash table data structure After the explanation part, we will do some exercices.</p>

#### What does the hash table mean?
<p style='text-align: justify;'>
A hash table store key-value pairs. The elements of the hash table are put in order based on the hash code of the key. The key is used to access items in the collection. To create an instance of the hash table in c#, we need to use the System Collections namespace that contains classes and interfaces. The hashtable class implements a few interfaces like **ICollection, IEnumerable, IDictionary, ICloneable, IDeserializationCallback, ISerializable**. These interfaces have differents responsibilities for instance, **ICollection** defines size, enumerator ... so, be curious about what is going on in the background.</p>

#### ICollection
```c#
public interface ICollection : IEnumerable
{
    int Count { get; }
    bool IsSynchronized { get; }
    object SyncRoot { get; }
    void CopyTo(Array array, int index);
}

```

<p style='text-align: justify;'>
Let's create, initialize and use some methods. I initialized a hashtable and added 4 elements into it in the code below.</p>

```c#
Hashtable myHashTable = new Hashtable();
myHashTable.Add("movie", "Inception");
myHashTable.Add("series", "Game of Thrones");
myHashTable.Add("blues", "I’ll Play the Blues for You");
myHashTable.Add("reggae", "Bob Marley");
```
**How to print out its keys?**

```c#
foreach (var item in myHashTable.Keys)
    {
        Console.WriteLine("The key " + item + " is stored in the myHashTable");
    }
```
Output:
<p style='text-align: justify;'>
The key blues is stored in the myHashTable<br>
The key movie is stored in the myHashTable<br>
The key series is stored in the myHashTable<br>
The key reggae is stored in the myHashTable
</p>

**How to print out its values?**
```c#
 foreach (var item in myHashTable.Values)
    {
        Console.WriteLine("The value '" + item + "' is stored in the myHashTable");
    }
```
Output:
<p style='text-align: justify;'>
The value 'Game of Thrones' is stored in the myHashTable<br>
The value 'Inception' is stored in the myHashTable<br>
The value 'I'll Play the Blues for You' is stored in the myHashTable<br>
The value 'Bob Marley' is stored in the myHashTable<br>
</p>

**How to check if one specific key exists in the collection?**
ContainKey() method search the key and return true if the key exists in myHashTable.
```c#
bool check = myHashTable.ContainsKey("movie");
Console.WriteLine(check);
```
### Warning

**Warning:** Microsoft docs recommends to use the generic Dictionary<TKey,TValue> class instead of **Hashtable**.

See you on the c# **heap Data Structures**!