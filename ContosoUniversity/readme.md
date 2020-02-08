# Tutorial: Get Started with Entity Framework 6 Code First using MVC 5
[link](https://docs.microsoft.com/zh-tw/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)


## Create the data model

1. 建立三個主要的類別: student, course, enrollment

Entity Framework interprets a property as a foreign key property 
if it's named <navigation property name><primary key property name> 
(for example, StudentID for the Student navigation property since the Student entity's primary key is ID). 
Foreign key properties can also be named the same simply <primary key property name> 
(for example, CourseID since the Course entity's primary key is CourseID).

## 