# Reno Tracker - Ex05 - Database Querying Based on Filters

> This is the **third** in a series of exercises where you will be building a website to manage information on renovations. **Reno Tracker** is a web application for those who want to keep information on home renovation projects within their business. To start application development, we will limit the data to maintain in a database to the client, job, material and labour.
>
> **This set is cumulative**; future exercises in this series will build upon previous exercises.

## Overview

A key aspect of the site is to allow users to search the database to find information on various renovation projects. Your task in this assignment is to provide that functionality.

Use the demos presented in class as a guide to implementing this exercise.

### Overview Query Page

Create an `Query.cshtml`/`Query.cshtml.cs` Razor Page. The Page Model class must declare in its constructor a dependency on the `JobServices` and `SupplyServices` classes. Details of your display can be found below. Be sure to add a menu item so that this page can be navigated to using the main menu; use the text "Query" for the link. Add the necessary services to the class library to support this page.

### Reno System 

**Entities & DAL**

In this exercise, you will be using **reverse engineering** to replace your existing entity and context classes. Select all tables when you do the reverse engineering. It is ***strongly*** advised that you review the class demonstration for this process.

**JobServices**

Create a new service class called `JobServices` in your BLL folder. This class will contain one service method to return the complete list of Jobs. This  list will be sorted alphabetically by Description. Remember to register your service class.

Query

```csharp
    _context.Jobs.OrderBy(x => x.Description).ToList();
```

**SupplyServices**

Create a new service class called `SupplyServices` in your BLL folder. This class will contain one service method to return the complete list of supplies for a specified job. The method will receive a filtering parameter for a specified job.  Remember to register your service class.

Query

```csharp
    _context.Supplies
      .Where(x => x.JobId == jobid);
```

### Query Page to search Supplies needed for a specific Job

The `Query` page will display  information on the supply data in an HTML table. Display the `Material`, `Quantity` and `MaterialCost` information. This query page will have Drop Down List filter showing the Job description. The page will two buttons: Search and Clear. Each button will require a page handler.


Only present the data (sample) as shown below:

| Material | Qty | Cost ($) |
|----------|-----|------|
| A/S Mainstream S/F R/H | 1 | 198.00 |
| MAXX Nextile 60L X 30W X 60H 4 Piece | 1 | 699.00   |
| MAXX Cocoon Acrylic Aerosens Bathtub | 1 | 2599.00   |
| CGC Drywall 1/2in 4X8 and screws | 10 | 327.20   |



To ensure that your web application works, build and run your project.
