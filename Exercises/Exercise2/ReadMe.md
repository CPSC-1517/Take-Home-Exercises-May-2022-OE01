# OOP Training

> This is the second of a set of exercises that follow the evolution of a program to manage renovation projects. This set is cumulative and will build upon previous exercises.

## Overview

Your task is to generate a set of simple data types to represent the primary objects for managing renovation projects.

For this exercise, place all the required data types in the namespace `RenoSystem` and ensure that they are `public`. Create your project as a Console Application (.NET 6). You have been supplied a Unit Tests project that will inform you if your work will meet specifications. **Ensure you follow the given class diagrams for the Unit Tests to work.**

### General Validation Rules

All validation is to be performed by throwing exceptions. Here are some general requirements.

- Exceptions must have meaningful error messages with keywords (ex: positive, minimum).
- Use `ArgumentException()` for parameter value errors.
- Error messages must include details about the limits for acceptable values.
- Measurements must always be positive and non-zero numbers. Measurements are to in whole number increments (eg: 254) (all measures are in metric centimeters).
- All string information must contain text. Null, empty, and plain white-space text is not allowed. Sanitize your strings by trimming the leading and trailing whitespace.
- Use constants for minimum values.

### The `Wall`

Extend the `Wall` class by adding the following methods.

- Add **`Parse`** and **`TryParse`** methods to instantiate a Wall from a string. The string's format is expected to match the formatting of the `ToString()` method.
  - In the `Parse` method, throw a [`FormatException`](https://docs.microsoft.com/dotnet/api/system.formatexception?view=net-5.0) if the supplied string does not match the expected format.
  - In the `TryParse` method, explicitly return a `bool` indicating if the parsing was successful. The parameters for this method are to be a `string` and an `out` parameter for the `Wall` type.
- Add method **`DeleteOpening()`**
  - This method will remove an existing opening in the wall replacing the opening with a type of None.
- Add method **`ReplaceOpening(Opening opening)`**
  - This method will replace the opening in the wall. Ensure the opening meets the 90% validation on wall openings. Ensure a opening parameter (`ArgumentNullException` message should indicate the parameter is missing/required) was pass into the method.
### The `Room`

Modify the greedy constructor to receive a List&lt;Wall&gt;. If there is a supplied List<Wall> set the Walls property to the supplied list; otherwise set the property to an empty List<Wall>. This is needed to have JSON file I/O to work correctly.

**NOTE: you WILL need to add a ` ,null` argument to each `new Room(...)` creation in your RenoUnitTestsEx1 RoomTests class.**

Modify the `AddWall(Wall wall)` method to ensure the following:

- Ensure the supplied object is not `null`. If it is, throw an `ArgumentNullException` with proper values for the parameter name and the error message.
- Enusre the plan identifier for the wall being added is unique for the room. Throw an `Exception` with the plan identifier value starting with the string **Duplicate plan identifier**.
  
Add method `RemoveWall(string planid)` 

- This method will locate and remove the wall matching the parameter. If the parameter value is missing throw an argument null exception. If the wall cannot be located, throw an argument exception message containing the supplied parameter in a string. Remove the wall if a matching wall exists.
### A Console I/O Driver : Program.cs

### Const FileNames

Create 3 const strings at the being of your program. These strings will be assigned the filename for your good csv file, good json file and your bad csv file. Use relative addressing to position the files in your RenoSystem folder relative to the location of your .exe file.
### Reading a csv routine

Create a text file (extension `.csv`) holding the comma-separated values for five good walls, one wall per line. At least: one wall must **not** have an opening, one wall must have a door opening and one wall must have a window opening.

Example line: `Brd1,367,244,White,Window,100,120,12`

Create a void method which will receive 2 parameters representing a filename (string) and an instance of room. Read all the lines using the [`System.File`](https://docs.microsoft.com/dotnet/api/system.io.file?view=net-5.0) class. Parse the read lines into individual walls using the `Wall.TryParse` method. Process **all** read lines and output any/all parsed exceptions. Add the valid walls to a new room.

#### Exception testing

Once you have the good 5 record CSV working, copy the file and intermix 3 bad records. One record will have a missing value (insufficent values on record). One record will have a bad value for the csv value (example a negative measurement). One record will have a duplicate wall name. Rerun your program.

### Writing a JSON file
Create a method which receives a string representing the JSON filename and an instance of `Room`. The method returns nothing (void).

 Save the room information [formatted as JSON](https://docs.microsoft.com/dotnet/api/system.text.json.jsonserializer?view=net-5.0) to a separate file. Use your good data from your csv file to write out.


### Reading a JSON file
Create a method which receives a string representing the JSON filename and returns an instance of `Room`.

 Read the room information [formatted as JSON](https://docs.microsoft.com/dotnet/api/system.text.json.jsonserializer?view=net-5.0) from the `JSON` file you wrote. Return the Room data from the method. Display the Room data after returning from the read method.

 **HINT:** Remember to place the annotation `[JsonInclude]` in front of your properties that are readonly (have only a get;).

### Display Current Room
Use the supplied routine to display the contents of a Room. 

----

## Evaluation

> ***NOTE:** Your code **must** compile. Solutions that do not compile will receive an automatic mark of zero (0).*
>
> If you are unable to get a portion of the assignment to compile, you should:
>
> - Comment out the non-compiling portion of code
> - Identify the non-compiling portion in the **Incomplete Requirements** heading, noting the item's
>   - File name (e.g.: "Account.cs")
>   - Line number(s)
>   - Compiler error number and general message

Your assignment will be marked based upon the following weights. See the [general rubric](../../ReadMe.md#generalized-marking-rubric) for details.

| Earning | Weight | Deliverable/Requirement | Comment |
| ---- | --------- | ------- | ------------- |
|   | 3 | Wall Modifications |    |
|   | 3 | Room Modifications |    |
|   | 3 | Driver and File I/O |   |
|   | 1 | CSV Files  of Walls (rows do **NOT** match given Unit Tests values)|    |
|  | -4 | Other concerns and penalities (Unit Testing does not compile/run; commits reflect incremental development) max -4 |   |
| ---- | ----- | --------- |  ------ |
|   | **10** | **Total Weight** | ------ |
| ---- | ----- | --------- | ------ |


----

## Credits


