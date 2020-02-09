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

# Implement CRUD Functionality with the Entity Framework in ASP.NET MVC

- Create a Details page
- Update the Create page
- Update the HttpPost Edit method
- Update the Delete page
- Close database connections
- Handle transactions

## Create a Details page

1. Edit : Views\Student\Details.cshtml


## Update the Create page

1. Edit : Controllers\StudentController.cs (Create Action)

An alternative way to prevent overposting that is preferred by many developers 
is to use view models rather than entity classes with model binding. 
Include only the properties you want to update in the view model

## Update HttpPost Edit method

1. Edit : Controllers\StudentConteroller.cs (Edit Action)

All columns of the database row are updated, 
including those that the user didn't change. 
If you only want individual fields to be updated in the database, 
you can set the entity to **EntityState.Unchanged** and set individual fields to EntityState.Modified.

## Update the Delete page

1. Edit : Controllers\StudentController.cs (Delete Action)


# Add sorting, filtering, and paging with the Entity Framework in an ASP.NET MVC application

## Add column sort links

1. Edit: Controllers\StudentController.cs (Index Action)
2. Edit: Views\Student\Index.cshtml (Add table header sort hyperlink)

## Add a Search box

1. Edit: Controllers\StudentController.cs (Index Action)
2. Edit: Views\Student\Index.cshtml (Add Search From)

## Add paging

1. Install-Package : PagedList.Mvc
2. Edit: Controllers\StudentController.cs (Index Action)
3. Edit: Views\Student\Index.cshtml (Add paging links to the Student index view)

The **null-coalescing operator** defines a default value for a nullable type; 
the expression (page ?? 1) means return the value of page if it has a value, or return 1 if page is null.

## Create an About page

1. Create ViewModel : ViewModels\EnrollmentDateGroup.cs
2. Edit : Controllers\HomeController.cs (About Action)
3. Edit : Views\Home\About.cshtml

# Use connection resiliency and command interception with Entity Framework in an ASP.NET MVC app

- Enable connection resiliency
- Enable command interception
- Test the new configuration

## Enable connection resiliency

1. Add : DAL\SchoolConfiguration.cs
2. Edit: Controllers\StudentController.cs (catch RetryLimitExceededException)

## Enable command interception

To test the connection resiliency feature,
you need a way to intercept queries that Entity Framework sends to SQL Server and 
replace the SQL Server response with an exception type that is typically transient.

In this section of the tutorial you'll learn how to use the Entity Framework's interception feature directly,
both for logging and for simulating transient errors.

1. Create a logging interface and class
2. Add : Logging\ILogger.cs
3. Add : Logging\Logger.cs

Create interceptor classes

4. Add : DAL\SchoolInterceptorLogging.cs
5. Add : DAL\SchoolInterceptorTransientErrors.cs
6. Edit: Global.asax












