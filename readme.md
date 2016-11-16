# .NET & Visual Studio

## IDE = _Interactive Development Environment_   

## When create a project for the web application using the Visual studio
  - When name the file use the same case as nameSpace camal case and conventionally name the file after the namespace
  - When create a class = create a new file
## Solution is a collection of the projects. Most apps have more than one project.  
  - Add source control check box put projects in the directory

## Then Choose which visual studio version to use

## Github ... choose gitignor file to Visual studio
 - add commit by go to file source control - commit
 - Solution Explore - we can view the detail of the changes before commit
 - Source Control -view history
 - to view all changes go to right click on the commit view commit detail
 - we can also revert the commit to previous commit and get the file that was deleted back
 - to push the changes to github ex: We create new branch, we can right click on the branch and click on publish to add to github
 - click on sync to update the commit of all the changes
 - we can also merge
 - if there's conflict ..we can also look at annotated to see who made the commit that has conflict

### Resources
Resources

- Share Your Projects with GitHub Destktop Workshop
- Git Basics Course
- Git Command Line Tools
- Up-For-Grabs.NET
- .NET Open Source Developer Projects


# .NET - create new application

```
create new PROJECT in powershell
md newproject
cd newproject
dotnet new (or dotnet new -t web //type can also get help by dotnet new --help)

- we need to restore some packages by telling what's pkges will be use"
- update project.json file by
dotnet restore
  - will install dependencies project.json need
dotnet run
  - compile the file

In Visual studio code (written in the language: TypeScript)
- run code .
  - call code . to open
    If write program
    {
      Console.WriteLine("Hello world");
      var name = Console.ReadLine();
      Console.WriteLine("Hello {0} welcome to c#", name)
      //Tthe {0}  will be replaced by name
      or can also write it this way instead
      Console.WriteLine($"Hello {name} welcome to c#");
    }
- will notice that it's a c# application
- will auto create vscode folder
Ctrl + ` will open up Command prompt(terminal or powershell)

- We will need a web server in order to see code in browser
- Go to project.json to add dependencies  in vscode
  - under dependencies of "Microsoft.NETCore.App"
  - Add after }
  -,
   "Microsoft.AspNetCore.Server.Kestrel": "1.0.1"(pick ther latest version) (Kestrel is a dotNet core web server)
   - in command line that open in the vs code. it'll run automatically dotnet restore when click restore
-After add the pkg, in Application type we need to save it in order to use it
  using: Microsoft.AspNetCore.Builder;
  using: Microsoft.AspNetCore.Hosting;
  using: Microsoft.AspNetCore.Http;
  *****Below would already be build in VS Studio Once type in using!
    public class Startup
    {
      public void Configure(IApplicationBuilder app) //Configure will set everything up
      {
        app.Run(
            Context =>
            {
              return context.Response.WriteAsync (=response.writeLine)
            }
          );//now we build our host we'll need to run our host
      }
    }
    in public static void Main()
    {then we need to set
      var host = new WebHostBuilder().UseKestrel()
      .UserStartup<Startup>()
      .Build(); (host web application Now we need to add class Startup above)

      //now we need to run the host in order to tell the program to run it (if not run it'll just show up in command linet)
    host.run();
    }
  -now the command line will say to look at localhost ...

  -when project is modified (change) then we need to stop and run it again

  -To refresh the page add tool "dotNetWatch" = a dependencies that will be use during the compile time
  add to project.json file by add tools Section
},
"tools": {
  "Microsoft.DotNet.Watcher.Tools": {
    "version": "1.0.0-*",
    "imports": "portable-net451+win*"
  }
}

run dotNet restore
run dotNet watch run

```
## How Kestrel works
- Browser make a call to IIS -> to Kestrel(to reload page) <-connect to dotNetCore
- IIS express = manage life cycle of the application
  - if the kestrel crash, IIS will bring it back (it can be switch btwn IIS & Kestrel to run - kestrel run the small parts)
  - there's IIS in project.json file
  -if program is edited while it's running will it change w/Kestrel?
    -No; if dotNetWatch is not running
    -but it'll change if change to IIS
    -this is how we break up the responsibility into smaller portion like Online store
    - IIS also run on diff localhost
# ASP.Net Core Middleware = most dependencies which are building block
  - Any ASP.Net that changes the pipeline from the moment the response goes in until the moment the response goes back is a piece of middleware

## To write specific route either "string" or int
    ...
    routeBuilder.MapGet("post/{postNumber:int}", context => context.Response.WriteAsync($"Blog post id: {context.GetRouteValue("postNumber")}"));
    //int is a rule/validation to limit input can only be int in order for the route name to work. Without int .. letter can be inputted. You can also give it more detail using RegExpression. If the input doesn't match the postNumber's rule, the web will break & show 404

    - *Debugging Route ...* **Remember that** _Order does matter, which one comes first can change everything. Route can be greedy; like "postNumber" w/o specifying that's it int only ... it'll take in everything b/c it just take it in as string_

# MVC is middleware b/c it's a pipeline
- when pic the Nuget .. don't get the MVC.core ..just use the MVC 
## more info go to .Net documentation

# Visual Studio Keyboard Shortcuts
| Command | Key
| ------ | :-------:
|Start |	F5
|Start Without Debugging |	Ctrl+F5
|Restart |	Ctrl+Shift+F5
|Run to Cursor |	Ctrl+F10
|Step Into |	F11
|Step Out |	Shift+F11
|Step Over |	F10
|Stop Debugging |	Shift+F5
|Select All |	Ctrl+A
|Select Current Word |	Ctrl+W
|Copy |	Ctrl+C
|Cut |	Ctrl+X
|Copy Entire Line |	Ctrl+C
|Cut Entire Line |	Ctrl+X
|Paste |	Ctrl+V
|Undo |	Ctrl+Z
|Redo |	Ctrl+Y
|Find |	Ctrl+F
|Find All References |	Shift+F12
|Find In Files |	Ctrl+Shift+F
|Find Next |	F3
|Find Previous |	Shift+F3
|Replace |	Ctrl+H
|Replace in Files |	Ctrl+Shift+H
|  Build Solution	| Ctrl+Shift+B
|Go To End of Document |	Ctrl+End
|Go To Beginning of Document |	Ctrl+Home
|Got To Matching Brace |	Ctrl+]
|Go To Next Word |	Ctrl+Right
|Go To Previous Word |	Ctrl+Left
|Go To Line |	Ctrl+G
|Go To Declaration |	Ctrl+F12
|Go To Definition |	F12
|Navigate Backwards |	Ctrl+-
|Navigate Forewards |	Ctrl+Shift+-
|Next Tab |	Ctrl+Alt+Page Down
|Previous Tab |	Ctrl+Alt+Page Up
|Quick Launch |	Ctrl+Q
|Complete Word |	Ctrl+Space
|List Members |	Ctrl+J
|Paremeter Info |	Ctrl+Shift+Space
|Peek at Definition |	Alt+F12
|Quick Info |	Ctrl+K, Ctrl+I
|Close Popup Window |	Esc
|Make Lowercase |	Ctrl+U
|Make Uppercase |	Ctrl+Shift+U
|Move Selected Lines Up |	Alt+Up
|Move Selected Lines Down |	Alt+Down
|Indent |	Tab
|Unindent |	Shift+Tab
|Format Document |	Ctrl+K, Ctrl+D
|Format Selection |	Ctrl+K, Ctrl+F
|Comment Section |	Ctrl+K, Ctrl+C
|Uncomment Section |	Ctrl+K, Ctrl+U
|Rename |	Ctrl+R, Ctrl+R
|Extract Method |	Ctrl+R, Ctrl+M
|Remove Parameters |	Ctrl+R, Ctrl+V
|Reorder Parameters |	Ctrl+R, Ctrl+O
| Compile	| Ctrl+F7
|Hold down shift to hightlight everything between the cursor and where the cursor ends up
|Zoom In / Zoom Out |	Ctrl+Scroll Wheel
