# Tutorial: Get Started with Entity Framework 6 Code First using MVC 5
[link](https://docs.microsoft.com/zh-tw/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)


## Create the data model

1. 建立三個主要的類別: student, course, enrollment

Entity Framework interprets a property as a foreign key property 
if it's named <navigation property name><primary key property name> 
(for example, StudentID for the Student navigation property since the Student entity's primary key is ID). 
Foreign key properties can also be named the same simply <primary key property name> 
(for example, CourseID since the Course entity's primary key is CourseID).

## Create the database context

1. 建立 DAL\SchooContext.cs

This code creates a DbSet property for each entity set. 
In Entity Framework terminology, an entity set typically corresponds to a database table, 
and an entity corresponds to a row in the table.

## Initialize DB with test data

1. 建立 DAL\SchoolInitializer.cs
2. 編輯 Web.config > entityFramework \ contexts \ context tag

Entity Framework can automatically create (or drop and re-create) a database for you 
when the application runs. 

You can specify that this should be done every time your application runs 
or only when the model is out of sync with the existing database. 

You can also write a Seed method that Entity Framework automatically calls after creating the database 
in order to populate it with test data.

The default behavior is to create a database only if it doesn't exist 

## Set up EF 6 to use LocalDB

1. 編輯 Web.config > connectionStrings

If you want to create the database in your App_Data folder, 
you could add AttachDBFilename=|DataDirectory|\ContosoUniversity1.mdf to the connection string.

The ContosoUniversity1.mdf and .ldf database files are in the %USERPROFILE% folder.

https://docs.microsoft.com/zh-tw/ef/ef6/modeling/code-first/workflows/new-database

## Create controller and views

1. Add : MVC 5 Controller with views, using Entity Framework

