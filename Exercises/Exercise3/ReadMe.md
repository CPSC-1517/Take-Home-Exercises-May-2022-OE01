# Reno Tracker - Project Setup and Form Input

> This is the **first** in a series of exercises where you will be building a website to manage information on renovations. **Reno Tracker** is a web application for those who want to keep information on home renovation projects within their business. To start application development, we will limit the data to maintain in a database to rooms. <!-- They accept data contributions from others so long as the data is in plain-text CSV format. -->
>
> **This set is cumulative**; future exercises in this series will build upon previous exercises.

## Overview

You are to create a **new** ASP.NET Core Web Application (Razor Pages) for this exercise. Create the application using Visual Studio 2022. Name your wep app project **`RenoWebApp`**. Name your solution **`RenoTracker`**. Place your work in your exercise repository.

To ensure that your web application works, build and run your project. A browser window should open using a localhost port (https://localhost:5001). 5001 is a port number and may differ on your machine.

The styling for your application is up to you. The template for the `web app` project has Bootstrap built in, but you can use any website styling you choose:

1. [**holiday**](https://holidaycss.js.org) 
1. [**d0css**](https://vvvkor.github.io/d0/) 
1. [**awsm.css**](https://igoradamenko.github.io/awsm.css/) 
1. [**Tailwind CSS**](https://tailwindcss.com/) 
1. [**Bootstrap**](https://getbootstrap.com/docs/4.3/getting-started/introduction//) 

More information is available in the [Appendix](#appendix) of these (1 - 4) specifications.

Add a `ReadMe.md` file in the `RenoWebApp` folder to record your known bugs for this project. For each exercise, you are expected to update the status of the application's known bugs in this read me file.

### Modify `Index.cshtml`

Modify the home page to include the following.

- The title of the site (**Reno Tracker**)
- A simple logo for the site
- One to two paragraph welcome and summary description of the site

### Add `Contact.cshtml` Page

Add a "Contact Us" page with a form (`method="POST"`) to allow people to send a message to us. The form must include the following (all fields are required). Use `<input>` elements (with appropriate labels) unless otherwise indicated.

- **User Email** (use `type="email"`)
- **Subject/Topic** (use a `<select>` element with the options of "Contributing", "Request Membership", "Bug Report")
- **Message Title** (use `type="text"`)
- **Message Body** (use a `<textarea>` element)
- **Send** button (use a `<button>` element)

Process the form's input by echoing back the user's email, selected topic, and message title on the same page. You do ***not*** have to actually send an email.

### Update the `_Layout.cshtml`

Put your name in the `<footer>` element for the copyright information. Also ensure that the menu navigation has the following items.

- A link to the home page (`/Index`) with the text "Home"
- A link to the contact page (`/Contact`) with the text "Contact Us"
- A link to the privacy page (`/Privacy`) with the text "Privacy"
- Change the *brand* (default of bootstrap css) from a text string to a thumbnail imagine 80 X 80 pixels. Other css styled menu must have a thumbnail imagine 80 X 80 pixels. NO thumbnail has been supplied, source your own image. If you are not using an image created by yourself, place an acknowledgement link on your `Privacy` page. 

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

| Earned | Weight | Deliverable/Requirement |  Comments |
| ---- | ----- | --------- | --------------- |
|  | 2 | `_Layout.cshtml` |   |
|  | 3 | `Contact.cshtml` |   |
|  | 2 | `Index.cshtml` |    |
|  | 1 | Project Setup |    |
|  | 1 | `ReadMe.md` |    |
|  | 1 | Appropriate Styling |   |
|  | -4 | Other concerns and penalities (appllication does not compile/run; commits reflect incremental development) max -4 |    |
| ---- | ------ | --------- |     |
|     | **10** | **Total Weight** |     |

----

## Appendix

Styling your site is up to you. However, if you decide to not use Bootstrap, it is recommended that you remove the contents of the `wwwroot\lib\` folder and modify the following *cshtml* pages to clean up your use of the `class=""` attributes in the HTML.

### Clean `_Layout.cshtml`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - WebApp</title>
    <!-- Your preferred stylesheet library here -->
    <link rel="stylesheet" href="~/css/site.css" />
</head>

<body>
    <header>
        <nav>

            <ul class="navbar-nav flex-grow-1">
                <li><a asp-area="" asp-page="/Index">WebApp</a></li>
                <li><a asp-area="" asp-page="/Privacy">Privacy</a></li>
            </ul>
        </nav>
    </header>
    <main role="main" class="pb-3">
        @RenderBody()
    </main>

    <footer>
        <div>
            &copy; 2021 - WebApp - <a asp-area="" asp-page="/Privacy">Privacy</a>
        </div>
    </footer>

    <!-- Your preferred javascript library here -->
    <script src="~/js/site.js" asp-append-version="true"></script>

    @await RenderSectionAsync("Scripts", required: false)
</body>

</html>
```

### Clean `Index.cshtml`

```html
@page
@model IndexModel
@{
    ViewData["Title"] = "Home page";
}

<h1>Welcome</h1>
<p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
```

### Clean `Error.cshtml`

```html
@page
@model ErrorModel
@{
    ViewData["Title"] = "Error";
}

<header>
    <h1>Error.</h1>
    <h2>An error occurred while processing your request.</h2>
</header>

@if (Model.ShowRequestId)
{
    <p>
        <strong>Request ID:</strong> <code>@Model.RequestId</code>
    </p>
}

<h3>Development Mode</h3>
<p>
    Swapping to the <strong>Development</strong> environment displays detailed information about the error that occurred.
</p>
<p>
    <strong>The Development environment shouldn't be enabled for deployed applications.</strong>
    It can result in displaying sensitive information from exceptions to end users.
    For local debugging, enable the <strong>Development</strong> environment by setting the <strong>ASPNETCORE_ENVIRONMENT</strong> environment variable to <strong>Development</strong>
    and restarting the app.
</p>
```

----

### Installing new lib(raries) in wwwroot

Installing new lib libraries start with right clicking your lib folder; selecting Add; then select Client-Side Library. This will bring up a dialog for you to select your desired libraries. Typically you will select your Provider and then enter the desired Library. The library will present a list as you type, thus, once you see the library you desire, you can select it.

#### Installing holiday

Good layout menus and form control

perferred method would be to use the a link in your _Layout file

#### Installing d0css

Good navigation menus but lacking in form control layout

perferred method would be to use the a link in your _Layout file

#### Installing AWSM.CSS

Good form control layout but limited navigation options

Provider unpkg
Library awsm.css

If you use the **awsm.css** library, you can bring in the stylesheet by placing code similar to the following in your `_Layout.cshtml` file's `<header>` tag. The awsm.css library also comes with various themes.

```html
<link href="/lib/awsm.css/dist/awsm.min.css" rel="stylesheet">
```
#### Installing TailWindCSS 

`WARNING` this is *not* a classless css, more flexable then bootstrap.

Provider cdnjs
Library tailwindcss

#### Replacement of default site.css 

#### Holiday css

`NOTE`: The **holiday.js.org** does not appear to require the `site.css` to have anything in it. (testing is still underway).

#### AWSM css

Here's a sample bit of styling you can place in your `site.css` file to replace its existing content. This styling increases the width and adds some menu styling based on awsm.

```css
body {
    max-width: 100%;
    margin: 0;
    padding: 0;
}

    body header, body main, body footer, body article {
        position: relative;
        max-width: 80rem;
        margin: 0 auto;
    }

    body > header {
        max-width: 100%;
        margin: 0;
    }

        body > header > nav {
            display: grid;
            grid-template-columns: auto 80rem auto;
            background-color: black;
            color: white;
            margin-top: 0;
            margin-bottom: 0;
        }

            body > header > nav > ul {
                margin: 1rem;
            }

nav > ul > li {
    margin-top: 0.25em;
}

body > header a, body > header a:visited {
    color: whitesmoke;
    font-weight: bold;
    text-decoration: none;
}

header > figure {
    height: 200px;
    overflow: hidden;
    margin-top: 0;
}

footer a {
    text-decoration: none;
}

header > nav > ul:last-child {
    text-align: right;
}

main > *:first-child {
    margin-top: 1rem;
}
```
