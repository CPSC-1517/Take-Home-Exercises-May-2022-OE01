# Reno Tracker - Ex06 - Query Paging, Page to Page data transfer, CRUD page. 

> This is the **fourth** in a series of series of exercises where you will be building a website to manage information on renovations. **Reno Tracker** is a web application for those who want to keep information on home renovation projects within their business. To start application development, we will limit the data to maintain in a database to the client, job, material and labour. They want to maintain a database of jobs, material and labour.
>
> **This set is cumulative**; future exercises in this series will build upon previous exercises.

## Overview

A key aspect of the site is to allow users to search the database to find information on renovation projects. This site will allow the user to maintain records on the database. Your task in this assignment is to provide that functionality.

Use the demos presented in class as a guide to implementing this exercise.

### Implementing of paging for a tabular query display

Modify the `Query.cshtml`/`Query.cshtml.cs` Razor Page. The tabular display of job supplies from Exercise 5 will implement a form of paging. Using the Paginator class demonstrated in your lessons, alter the Supplies display so that only 5 rows are shown at a time.

You will need to alter your service query method to accomondate the paginator.

### Page to Page Data transfer

Alter the Supplies display line to contain a link which will transfer control to another Razor Page called `CRUDPage.cshtml`. The data to transfer will be the SupplyId value.

Add a button, called `New`, to the `Query.cshtml` page which will transfer contol to the `CRUDPage.cshtml` page. The button text may have text of your choice. No data will be transfered with this redirection.

### CRUDPage

***Do not add an item on the menu for this page. It should only be reached via the `Query.cshtml` page.***

Create a Razor Page called `CRUDPage.cshtml`. This page will be used to maintain the job Supplies database table. Maintenance will consist of a) adding new job supply; b) updating existing job supply; and c) delete a job supply. Create a form that will display all fields of the record. Use a select control for the JobId (display the job description). Use an input control of number for the Quantity and MaterialCost. The SupplyId control will be disabled. The delete button must have a confirmation message attached to the button. Add a button to return to the `Query` page and a button to clear the form.

Add appropriate service methods to your Supply services to a) obtain a specific Supply record (see supplied query), b) add a new record to the Supply table, c) update an existing record on the Supply table and d) physically remove an existing record from the Supply table.

Query: SupplyServices.GetByID

```
 Supply info = _context.Supplies
                .Where(x => x.SupplyId == supplyid)
                .FirstOrDefault();
```

### Validation

Ensure you include validation display controls for each CRUD field. Adjust the default validation annotations with custom error messages.


To ensure that your web application works, build and run your project.

## Evaluation

> ***NOTE:** Your code **must** compile. Solutions that do not compile will receive an automatic mark of zero (0).*
>
> If you are unable to get a portion of the assignment to compile, you should:
>
> - Comment out the non-compiling portion of code
> - Identify the non-compiling portion under a **Incomplete Requirements** heading on your `index.cshthml` page, noting the item's
>   - File name (e.g.: "Account.cs")
>   - Line number(s)
>   - Compiler error number and general message

Your assignment will be marked based upon the following weights. 

| Earned | Weight | Deliverable/Requirement | Comments |
| ------ | ---- | --------- | ------- |
|  | 3 | `CRUD.cshtml` setup of form (all Supply fields) |    |
|  | 2 | `CRUD.cshtml` dropdown list for JobId |     |
|  | 1 | `Supply.cs` custom messages for client side validation in entity |     |
|  | 1 | `CRUD.cshtml` display of client side valiation messages |    |
|  | 1 | `CRUD.cshtml.cs` Search and Clear buttons process |    |
|  | 1 | `CRUD.cshtml.cs` New button process |    |
|  | 1 | `CRUD.cshtml.cs` Update button process |    |
|  | 2 | `CRUD.cshtml.cs` Delete button process with confirmation prompt |     |
|  | 2  | `CRUD.cshtml.cs` user friendly error handling |   |
|  | 2 | `RollingStock.cs` Add method |   |
|  | 2 | `RollingStock.cs` Update method |    |
|  | 2 | `RollingStock.cs` Deactivate (delete) method update InService to be false |     |
|  | (-5)  | `Other concerns` penalties for other problems max -5 |   |
|  | **20** | **Total Weight** |   |

----

Other Concerns
