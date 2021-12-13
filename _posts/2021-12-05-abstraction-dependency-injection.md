---
layout: post
title: Coding Challenge 10
subtitle: C# Interfaces, abstraction and N-Tier Architecture
tags: [c#,object oriented programming, solid principles,factory pattern,interface, Abstract, İnheritance, school management system]
comments: false
---

<p style='text-align: justify;'>
Today, we are going to create a project named School Management System by applying SOLID Principles. Then, we will use Factory pattern. 
First we created a blank solution to implement layered architecture. After creating a blank solution, open "Solution Explorer" and right-click on the project and add the following class libraries:</p>

* Business
* DataAccess
* Entities

Please do not forget that after learning new things, we will add new properties and new patterns to this project. 

#### Why do we need layers?
<p style='text-align: justify;'>
When you create all classes without layers, It will be hard to manage all files. Actually, we separate them to manage better.</p>

### Entities
<p style='text-align: justify;'>
We start creating  two entities named <b>Student</b> Class and <b>Instructor</b> Class. Each of them has the properties belove. In this project, we do not use Entity framework.IEntity is just an interface.</p>

#### Student Class
```c#
public class Student : IEntity
{
    public short ID { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Tel { get; set; }
    public string NationaltyId { get; set; }
    public byte GNO { get; set; }
    public string Classroom { get; set; }
}
```

####  Instructor Class

```c#
public class Instructor:IEntity
{
    public short ID { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Tel { get; set; }
    public string NationaltyId { get; set; }
    public string Branch { get; set; }
}
```

### DataAccess 
<p style='text-align: justify;'>
Before creating interfaces, it's important to understand why we add only single responsibility to a class or to a method. Let's discover Solid principles together!
Imagine that you created a software project and it is getting bigger and bigger, after a while you notice that you repeat yourself or write the same codes in similar classes or one change impacts other codes. 
What should we have done to avoid these repetitions? These problems have been thought by <b>Robert C. Martin</b> who developed SOLID principles in 2000 to make a software project flexible, mobile and stronger.<br>
<b>Solid Principles:</b> </p>

* <b>S</b>ingle responsiblity principle
* <b>O</b>pen closed principle
* <b>L</b>iskov substitution principle
* <b>I</b>nterface segragetion principle
* <b>D</b>ependency inversion principle

<p style='text-align: justify;'>
<b>Single responsibility principle</b>:  Each class should have only one job. <br>
<b>Open closed principle</b>: Open for extensions but closed for modification.<br>
<b>Liskov substitıtion principle</b> is named by a woman mathematician Barbara Liskov. This principle says that every subclass or derived class should be exchangeable for their base or parent class. <br>
<b>Interface segregation principle</b>: It is used to avoid unnecessary methods or properties in a class. A client should not be forced to depend on methods they do not use.<br>
<b>Dependency inversion principle</b>: We try to decrease dependencies between high-level-module and low-level-module. The high-level module must not depend on the low-level module, but they should depend on abstractions.</p>




<p style='text-align: justify;'>
Let's continue create other classes that we need. Once you have created them all, you will see the project as a whole.</p>


### Abstract Folder in DataAccess Layer

#### IEntityRepository 
```c#
public interface IEntityRepository<T> where T:class,IEntity,new()
{
    List<T> GetAll(Expression<Func<T,bool>> filter =null);
    T Get(Expression<Func<T, bool>> filter);
    void Add(T entity);
    void Delete(T entity);
    void Update(T entity);
}
```

#### IInstructorDal
```c#
public interface IInstructorDal:IEntityRepository<Instructor>
{
}
```

#### IInstructorDal
```c#
public interface IStudentDal:IEntityRepository<Student>
{
}
```


### Concrete Folder >> EntityFramework
 
#### IInstructorDal
```c#
public class EfStudentDal : IStudentDal
{
    public void Add(Student entity)
    {
        using (SchoolContext context = new SchoolContext())
        {
            var addedEntity = context.Entry(entity);
            addedEntity.State = EntityState.Added;
            context.SaveChanges();
        }
    }

    public void Delete(Student entity)
    {
        using (SchoolContext context = new SchoolContext())
        {
            var deletedEntity = context.Entry(entity);
            deletedEntity.State = EntityState.Deleted;
            context.SaveChanges();
        }
    }

    public Student Get(Expression<Func<Student, bool>> filter)
    {
        using (SchoolContext context = new SchoolContext())
        {
            return context.Set<Student>().SingleOrDefault(filter);
        }
    }

    public List<Student> GetAll(Expression<Func<Student, bool>> filter = null)
    {
        using (SchoolContext context = new SchoolContext())
        {
            return filter == null ? context.Set<Student>().ToList() :
                    context.Set<Student>().Where(filter).ToList();
        }
    }

    public void Update(Student entity)
    {
        using (SchoolContext context = new SchoolContext())
        {
            var updatedEntity = context.Entry(entity);
            updatedEntity.State = EntityState.Modified;
            context.SaveChanges();
        }
    }
}
```
<p style='text-align: justify;'>
Now it's your turn:) Create an EfInstructoralDal. Then, visit my GitHub repository to see the whole project. </p>
<a></a>

<a href="https://github.com/baristutakli/">Visit my Github account</a>
